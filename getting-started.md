---


copyright:
  years: 2020
lastupdated: "2020-09-30"

keywords: Cloud Pak® for Security, Install

subcollection: writing


---


{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:note: .note}
{:external: target="_blank" .external}


# Getting started with IBM Cloud Pak® for Security
{: #getting-started}

IBM Cloud Pak® for Security provides a platform to quickly integrate your existing security tools to generate deeper insights into threats across hybrid, multicloud environments.
{:shortdesc}

The IBM Cloud Pak® for Security platform uses an infrastructure-independent common operating environment that can be installed and run anywhere. It comprises containerized software pre-integrated with Red Hat OpenShift enterprise application platform, which is trusted and certified by thousands of organizations around the world.

IBM Cloud Pak® for Security can connect disparate data sources — to uncover hidden threats and make better risk-based decisions — while leaving the data where it resides. By using open standards and IBM innovations, IBM Cloud Pak® for Security can securely access IBM and third-party tools to search for threat indicators across any cloud or on-premises location. Connect your workflows with a unified interface so you can respond faster to security incidents. Use IBM Cloud Pak® for Security to orchestrate and automate your security response so that you can better prioritize your team's time.

## What's inside this Cloud Pak
{: #included}

<!-- Component section: REQUIRED
The component section includes a list of the offerings with descriptions included in the Cloud Pak. Brief description about why this product is in the Cloud Pak and how the customer can use it. Also include where a user can find more information on each offering by including a link to its documentation.  -->

IBM Cloud Pak® for Security includes the following applications.
  
  - IBM Security Threat Intelligence Insights is an application that delivers unique, actionable, and timely threat intelligence. The application provides most of the functions of IBM X-Force® Exchange.
  - IBM Security Data Explorer is a platform application that enables customers to do federated search and investigation across their hybrid, multi-cloud environment in a single interface and workflow.
  - IBM Security Case Management for IBM Cloud Pak® for Security provides organizations with the ability to track, manage, and resolve cybersecurity incidents.
  - IBM Security Orchestration & Automation application is integrated on IBM Cloud Pak® for Security to provide most of the IBM Resilient Security Orchestration, Automation, and Response Platform feature set.
  - IBM QRadar® Security Intelligence Platform is offered as an on-premises solution and delivers intelligent security analytics, enabling visibility, detection, and investigation for a wide range of known and unknown threats.
  
For more information see, [Knowledge Center](https://www.ibm.com/support/knowledgecenter/SSTDPP_1.4.0/platform/docs/scp-core/overview.html){: external}.


## Before you begin
{: #prereqs}
<!-- Before you begin prereqs: REQUIRED
Include a prerequisites sections for any prerequisites to be met. Use H3s for each applicable section.
Example: -->

Review the prerequisites so that you can successfully install the Cloud Pak® for Security.

* A single-zone cluster [Red Hat OpenShift on IBM Cloud Version >=4.4.14 or >=4.5.8](https://cloud.ibm.com/kubernetes/catalog/about?platformType=openshift). 

* Admin access to the cluster.

* A valid Transport Layer Security (TLS) certificate and certificate key for the Cloud Pak® for Security Fully Qualified Domain Name (FQDN). You can use the Transport Layer Security (TLS) certificates from your IBM Cloud OpenShift cluster. For more information, see [Domain name and TLS certificate](https://www.ibm.com/support/knowledgecenter/SSTDPP_1.4.0/platform/docs/security-pak/find-ibmcloud-fqdn.html){: external}.


### Minimum hardware requirements
{: #required-capacity}
<!-- Capacity section: REQUIRED.
All Cloud Paks specify the minimum cluster requirements. List these here so a customer can ensure to have a cluster that meets the minimum capacity. -->

| Node type | Number of nodes | CPU | RAM | Storage |
| --------- | ----------- | ----------- | ----------- | ------- |
| Worker | 3 | 8 cores | 32 GB | 120 GB |
{: caption="Table 1. Resource requirements for Cloud Pak for Security" caption-side="top"}

For more information, see [hardware requirements](https://www.ibm.com/support/knowledgecenter/SSTDPP_1.4.0/platform/docs/security-pak/hardware.html){: external}.

### Minimum storage requirements

The system disk requirements do not include the persistent storage requirements. The persistent storage requirement for IBM Cloud Pak® for Security is 1 TB. For more information, see [persistent storage requirements](https://www.ibm.com/support/knowledgecenter/SSTDPP_1.4.0/platform/docs/security-pak/persistent_storage.html){: external}.

### Purchasing a license
{: #license-entitlement}

Before you can install IBM Cloud Pak® for Security, you must purchase a license. Purchase a license, also known as an entitlement, through [IBM Passport Advantage](https://www.ibm.com/software/passportadvantage/index.html){: external}.

## Step 1. Finding the Cloud Pak in the IBM Cloud Catalog
{: #catalog}

<!-- Catalog discovery: REQUIRED
Describe how to find the Cloud Pak in the catalog-->

Go to the [IBM Cloud Catalog](https://cloud.ibm.com/catalog), and select the **Cloud Paks** filter. Then, select the **IBM Cloud Pak® for Security** tile.

## Step 2. Configuring the installation
{: #configure}

1. Select the Cloud Pak version to install.

2. Create or select a [RedHat Openshift >=4.4.14 or >=4.5.8 cluster](https://cloud.ibm.com/kubernetes/catalog/about?platformType=openshift) for your installation.

3. Create or select a Project or Namespace.

4. Configure your workspace.

5. Set your deployment values as outlined in the following tables. 

6. Ensure that you have acquired a license for the IBM Cloud Pak® for Security deployment.

7. Confirm that you have read and agreed to the license.

| Required values | Description | 
| --------- | ----------- |
| adminUserId | Cloud Pak for Security Administrator |
| cert | Cloud Pak for Security Domain TLS Certificate |
| certKey | Cloud Pak for Security Domain TLS Certificate Key |
| domain | Cloud Pak for Security Application URL |
{: caption="Table 2. Required deployment parameters for Cloud Pak for Security" caption-side="top"}

| Optional values  | Description | Default
| --------- | ----------- | ----------- |
| storageClass | Cloud Pak for Security Default Storage Class | ibmc-block-gold |
| customCA | Custom Certificate of Authority (CA) for Non-Trusted Certificate  | nil | 
| securityAdvisor | Deploy Security Advisor | Disable |
| toolboxStorageClass | Cloud Pak for Security Toolbox Storage Class | Value set in `storageClass` |
| toolboxStorageSize | Cloud Pak for Security Toolbox Storage Size | 100 GB |
| imagePullPolicy | Cloud Pak for Security Image Pull Policy | IfNotPresent |
| defaultAccountName | Cloud Pak for Security Account Name | Cloud Pak For Security |
{: caption="Table 3. Optional deployment parameters for Cloud Pak for Security" caption-side="top"}

## Step 3. Install your IBM Cloud Pak® for Security
{: #install}

When all the required parameters are set, click **Install**.

## Step 4. Monitor your installation in the workspace
{: #workspace}

After you start the installation, you are brought to the Schematics workspace for your Cloud Pak. You can track progress by viewing the logs. Go to the **Activity** tab, and click **View logs**.

## Step 5. Retrieve IBM Common Services® login details
{: #password}

The installation takes approximately 1.5 hours to complete and includes the installation of IBM Cloud Platform Common Services®.

Use the following commands to retrieve IBM Common Services® hostname, default username and password:

Hostname:

```
oc -n ibm-common-services get route | grep cp-console | awk '{print $2}'
```

Username:

```
oc -n ibm-common-services get secret platform-auth-idp-credentials -o jsonpath='{.data.admin_username}' | base64 --decode 
```

Password:

```
oc -n ibm-common-services get secret platform-auth-idp-credentials -o jsonpath='{.data.admin_password}' | base64 --decode

```

These login details are required to access Common Services and configure your Lightweight Directory Access Protocol (LDAP) directory.

## Next steps
{: #next-steps}

1. [Configure LDAP authentication](https://www.ibm.com/support/knowledgecenter/SSTDPP_1.4.0/platform/docs/security-pak/ldap-connect.html){: external}.
2. Log in to Cloud Pak® for Security by using the value of the `domain` parameter that is assigned during deployment and the user value that is assigned in the parameter `adminUserId`.
3. [Add users to Cloud Pak® for Security](https://www.ibm.com/support/knowledgecenter/SSTDPP_1.4.0/platform/docs/scp-core/users.html){: external}.
4. Install the [IBM® Security Orchestration & Automation license](https://www.ibm.com/support/knowledgecenter/SSTDPP_1.4.0/platform/docs/security-pak/license_UI.html){: external}.
If you choose Orchestration & Automation as part of your Cloud Pak® for Security bundle, you must install your Orchestration & Automation license to access the complete orchestration and automation capabilities that are provided by Orchestration & Automation.
5. [Configure data sources](https://www.ibm.com/support/knowledgecenter/SSTDPP_1.4.0/platform/docs/scp-core/data-sources.html){: external}.

## Uninstalling the IBM Cloud Pak® for Security
{: #uninstall}

Uninstalling the IBM Cloud Pak® for Security from the console:

1. Enter the workspace of your installed IBM Cloud Pak® for Security.

2. In the upper right corner, click **Actions**. 

3. To trigger a delete, click **Delete**.

3. Choose `Delete workspace` and `Delete all associated resources` and input the name of the workspace to confirm. To delete the workspace, click **Delete**.

4. Wait for the Cloud Pak to finish uninstalling.

5. Verify that the IBM Cloud Pak® for Security is uninstalled: Access the Openshift web console and verify that the components that are related to the IBM Cloud Pak® for Security, such as any related pods, are no longer installed.

## Upgrading IBM Cloud Pak® for Security

The steps to upgrade are the same as the steps to install. The process automatically detects an older version and initiates an upgrade.

For information about working with your Cloud Pak®, see [Knowledge Center](https://www.ibm.com/support/knowledgecenter/SSTDPP_1.4.0){: external}.
