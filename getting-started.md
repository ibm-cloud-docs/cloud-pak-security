---


copyright:
  years: 2020,2021
lastupdated: "2021-07-29"

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

The IBM Cloud Pak® for Security platform uses an infrastructure-independent common operating environment that can be installed and run anywhere. It comprises containerized software pre-integrated with Red Hat® OpenShift® enterprise application platform, which is trusted and certified by thousands of organizations around the world.

IBM Cloud Pak® for Security can connect disparate data sources — to uncover hidden threats and make better risk-based decisions — while leaving the data where it resides. By using open standards and IBM innovations, IBM Cloud Pak® for Security can securely access IBM and third-party tools to search for threat indicators across any cloud or on-premises location. Connect your workflows with a unified interface so you can respond faster to security incidents. Use IBM Cloud Pak® for Security to orchestrate and automate your security response so that you can better prioritize your team's time.

## What's inside this Cloud Pak
{: #included}

<!-- Component section: REQUIRED
The component section includes a list of the offerings with descriptions included in the Cloud Pak. Brief description about why this product is in the Cloud Pak and how the customer can use it. Also include where a user can find more information on each offering by including a link to its documentation.  -->

IBM Cloud Pak® for Security includes the following offerings.
  
  - IBM® Security Threat Intelligence Insights is an application that delivers unique, actionable, and timely threat intelligence. The application provides most of the functions of IBM X-Force® Exchange.
  - IBM® Security Data Explorer is a platform application that enables customers to do federated search and investigation across their hybrid, multi-cloud environment in a single interface and workflow.
  - IBM® Security Case Management for IBM Cloud Pak® for Security provides organizations with the ability to track, manage, and resolve cybersecurity incidents.
  - IBM® Security Orchestration & Automation application is integrated on IBM Cloud Pak® for Security to provide most of the IBM Resilient Security Orchestration, Automation, and Response Platform feature set. If you have an Orchestration & Automation license, you can choose between the stand-alone version on a virtual appliance, or the application on Cloud Pak for Security. 
  - IBM® QRadar® is offered as a stand-alone on-premises solution and delivers intelligent security analytics, enabling visibility, detection, and investigation for a wide range of known and unknown threats. Event analytics ingest, parse, normalize, correlate, and analyze log and event data to detect indicators of threats. Flow analytics collect, extract, and normalize valuable network flow data and packet metadata to augment log-based security insights.
  - IBM® QRadar® Proxy application provides communication between IBM Cloud Pak for Security and IBM QRadar or QRadar on Cloud. This communication uses APIs to pull powerful QRadar data into the QRadar Security Information and Event Management (SIEM) dashboards.
  - IBM® QRadar® User Behavior Analytics is an application for detecting insider threats in your organization. User Behavior Analytics, used in conjunction with the existing data in your QRadar system, can help you generate new insights around users and user risk. 
  - IBM® Security Risk Manager application provides early visibility into potential security risks by correlating insights from multiple vectors so that you can prioritize risks to take appropriate remedial actions. 
  - IBM® Security Threat Investigator is an application that automatically analyzes and investigates cases to help determine the criticality of exposure, how many systems are at risk, and the level of remediation effort that is required.  
  - IBM® Security Guardium Insights is a stand-alone collaborative, robust data security platform that is designed help to unify and modernize the security operations center (SOC). Collected data can be shared with Cloud Pak for Security.
  - IBM® Security Guardium Data Protection is a data activity monitoring and compliance reporting solution that is purpose-built to protect sensitive data stored across platforms. 
  - IBM® Security Guardium Vulnerability Assessment solution identifies threats and security holes that might be used by malicious actors to access sensitive data. The solution recommends concrete actions to strengthen security.
    
For more information, see [IBM Documentation](https://www.ibm.com/support/knowledgecenter/SSTDPP_1.7.0/docs/scp-core/overview.html){: external}.

## Purchasing a license
{: #license-entitlement}

Before you can install IBM Cloud Pak® for Security, you must purchase a license. Purchase a license, also known as an entitlement, through [IBM Passport Advantage](https://www.ibm.com/software/passportadvantage/index.html){: external}.

For more information, see [Licensing and entitlement](https://ibmdocs-test.mybluemix.net/docs/en/cloud-paks/cp-security/1.7.0?topic=planning-licensing){: external}.

## Before you begin
{: #prereqs}
<!-- Before you begin prereqs: REQUIRED
Include a prerequisites sections for any prerequisites to be met. Use H3s for each applicable section.
Example: -->

Review the prerequisites so that you can successfully install the IBM Cloud Pak® for Security.

* A single-zone cluster [Red Hat OpenShift on IBM Cloud Version 4.6.X or 4.7.X](https://cloud.ibm.com/kubernetes/catalog/about?platformType=openshift). 

* Administrator access to the Kubernetes cluster for both platform and service access policies. For more information, see [Assigning cluster access](https://cloud.ibm.com/docs/containers?topic=containers-users#access_policies).

* You can install IBM Cloud Pak® for Security as a subdomain of your IBM Cloud OpenShift cluster by not specifying a `domain` while configuring your deployment. If you choose this method, Cloud Pak® for Security uses the Transport Layer Security (TLS) certificates from your IBM Cloud OpenShift cluster and the ingress subdomain is used to access IBM Cloud Pak® for Security.

* A valid TLS certificate and certificate key for the Cloud Pak® for Security Fully Qualified Domain Name (FQDN). You can use the TLS certificates from your IBM Cloud® OpenShift cluster. For more information, see [Domain name and TLS certificate](https://www.ibm.com/support/knowledgecenter/SSTDPP_1.7.0/docs/security-pak/tls_certs.html){: external}.



### Minimum hardware requirements
{: #required-capacity}

<!-- Capacity section: REQUIRED.
All Cloud Paks specify the minimum cluster requirements. List these here so a customer can ensure to have a cluster that meets the minimum capacity. -->

| Node type | Number of nodes | CPU | RAM | Storage |
| --------- | ----------- | ----------- | ----------- | ------- |
| Worker | 4 | 8 cores | 32 GB | 120 GB |
{: caption="Table 1. Resource requirements for Cloud Pak for Security" caption-side="top"}

**Important:** The hardware requirements is validated automatically by the IBM Cloud catalog prior to the deployment.

### Minimum storage requirements

The system disk requirements do not include the persistent storage requirements. The persistent storage requirement for IBM Cloud Pak® for Security is 1 TB. For more information, see [persistent storage requirements](https://www.ibm.com/support/knowledgecenter/SSTDPP_1.7.0/docs/security-pak/persistent_storage.html){: external}.


## Step 1. Finding the Cloud Pak in the IBM Cloud Catalog
{: #catalog}

<!-- Catalog discovery: REQUIRED
Describe how to find the Cloud Pak in the catalog-->

Go to the [IBM Cloud Catalog](https://cloud.ibm.com/catalog), and select the **Cloud Paks** filter. Then, select the **IBM Cloud Pak® for Security** tile.

## Step 2. Configuring the installation
{: #configure}

1. Select the IBM Cloud Pak® for Security 1.7.2.0 version to install.

2. Create or select a [RedHat OpenShift 4.6.X or 4.7.X cluster](https://cloud.ibm.com/kubernetes/catalog/about?platformType=openshift) for your installation.

3. Create or select a Project or Namespace.

4. Configure your workspace.

5. Set your deployment values as outlined in the following tables. 

6. Ensure that you have acquired a license for the IBM Cloud Pak® for Security deployment.

7. Confirm that you have read and agreed to the license.

| Required values | Description | 
| --------- | ----------- |
| adminUserId | The user that is to be assigned as an `Administrator` in the Cloud Pak for Security installation. The `Administrator` user must exist in an Lightweight Directory Access Protocol (LDAP) directory that you will setup in the post installation task [LDAP connection](https://www.ibm.com/support/knowledgecenter/SSTDPP_1.7.0/docs/security-pak/ldap-connect.html) section; or is a user that is added and authenticated using the IBM Cloud account in which the cluster was created. |
{: caption="Table 2. Required deployment parameters for Cloud Pak for Security" caption-side="top"}

**Note:** The user that you provide as `adminUserId` must be the admin for the LDAP directory with an email address in the LDAP directory. Take note of the user that you provide as that user will be required as the initial user to log in to IBM Cloud Pak® for Security.

| Optional values  | Description | Default |
| --------- | ----------- | ----------- |
| domain | Cloud Pak for Security application URL. If blank, OpenShift ingress subdomain and certificates are used. The CP4S route will be cp4s.{your-cluster-ingress-subdomain}. |  | 
| cert | Cloud Pak for Security domain TLS certificate. Required when `domain` is set. |  | 
| certKey | Cloud Pak for Security domain TLS certificate key. Required when `domain` is set. | | 
| customCA | Custom Certificate of Authority (CA) for untrusted certificate.   |  | 
| OpenshiftAuthentication | Enable OpenShift integration with IBM Security Verify. | Disable |
| storageClass | Cloud Pak for Security default storage class. | ibmc-block-gold |
| securityAdvisor | Deploy IBM Cloud® Security Advisor. | Disable |
| backupStorageClass | Cloud Pak for Security backup storage class. | Value set in `storageClass` |
| backupStorageSize | Cloud Pak for Security backup storage size. | 500 GB |
| imagePullPolicy | Cloud Pak for Security image pull policy | Always |
| defaultAccountName | Cloud Pak for Security account name. | Cloud Pak For Security |
{: caption="Table 3. Optional deployment parameters for Cloud Pak for Security" caption-side="top"}
  
For more information about certificates, see [Domain name and TLS certificate](https://www.ibm.com/support/knowledgecenter/SSTDPP_1.7.0/docs/security-pak/tls_certs.html){: external}.  

## Step 3. Install your IBM Cloud Pak® for Security
{: #install}

When all the required parameters are set, click **Install**.

## Step 4. Monitor your installation in the workspace
{: #workspace}

From this stage, the installation will take approximately 1.5 hours to complete which includes the installation of IBM Cloud Pak foundational services. After you start the installation, you are brought to the Schematics workspace for your Cloud Pak. You can track progress by viewing the logs. Go to the **Activity** tab, and click **View logs**.

## Step 5. Retrieve foundational services login details
{: #password}

Use the following commands to retrieve IBM Cloud Pak foundational services hostname, default username, and password:

Hostname:

```
oc -n ibm-common-services get route | grep cp-console | awk '{print $2}'
```
{: codeblock}

Username:

```
oc -n ibm-common-services get secret platform-auth-idp-credentials -o jsonpath='{.data.admin_username}' | base64 --decode 
```
{: codeblock}

Password:

```
oc -n ibm-common-services get secret platform-auth-idp-credentials -o jsonpath='{.data.admin_password}' | base64 --decode
```
{: codeblock}

These login details are required to access foundational services and configure your LDAP directory.

## Next steps
{: #next-steps}

1. If the `adminUserId` you provided is a user ID that you added and authenticated by using the IBM Cloud account that is associated with the cluster and `OpenShiftAuthentication` was enabled, go to step 2. Otherwise, [Configure LDAP authentication](https://www.ibm.com/support/knowledgecenter/SSTDPP_1.7.0/docs/security-pak/ldap-connect.html){: external} and ensure that the `adminUserId` that you provided exists in the LDAP directory.
2. Log in to Cloud Pak® for Security using the domain and the `adminUserId` that you provided during installation. The `domain`, also known as `application URL`, can be retrieved by running the following command:
    ```bash
    oc get route isc-route-default --no-headers -n <CP4S_NAMESPACE> | awk '{print $2}'
    ```
    {: codeblock}

    Select `Enterprise LDAP` in the login screen if you are logging in using an LDAP you connected to Foundational Services, otherwise use `OpenShift Authentication` if it is enabled.

3. [Add users to Cloud Pak® for Security](https://www.ibm.com/support/knowledgecenter/SSTDPP_1.7.0/docs/scp-core/users.html){: external}.
4. Install the [IBM® Security Orchestration & Automation license](https://www.ibm.com/support/knowledgecenter/SSTDPP_1.7.0/docs/security-pak/license_UI.html){: external}.
If you choose Orchestration & Automation as part of your Cloud Pak® for Security bundle, you must install your Orchestration & Automation license to access the complete orchestration and automation capabilities that are provided by Orchestration & Automation.
5. [Configure data sources](https://www.ibm.com/support/knowledgecenter/SSTDPP_1.7.0/docs/scp-core/data-sources.html){: external}.

## Uninstalling the IBM Cloud Pak® for Security
{: #uninstall}

Uninstalling the IBM Cloud Pak® for Security from the console:

1. Go to the workspace where you installed IBM Cloud Pak® for Security.

2. On the workspace toolbar, click the **Actions** button. 

3. To uninstall, click **Destroy**.

3. To confirm, enter the name of the workspace to uninstall. To uninstall, click **Destroy**.

4. Wait for the Cloud Pak to finish uninstalling.

5. To verify that the IBM Cloud Pak® for Security is uninstalled, access the OpenShift web console and verify that the components that are related to the IBM Cloud Pak® for Security, such as any related pods, are no longer installed.

**Important:** The uninstall action does not remove the IBM Cloud Pak® foundational services that are installed in the cluster. To manually remove the foundational services, see [Uninstalling foundational services](#uninstall-cs).

## (Optional) Uninstalling foundational services
{: #uninstall-cs}

To uninstall the IBM Cloud Pak® foundational services that are installed in the cluster, complete the following procedure. This procedure requires you to have the `oc` and `cloudctl` CLI tools installed in your local machine. To install the required CLI tools, follow the steps in [Installing developer tools](https://www.ibm.com/docs/en/cloud-paks/cp-security/1.7.2?topic=tasks-installing-developer-tools){: external}.
1. Download and extract the IBM Cloud Pak® for Security archive file:
    ```bash
    cloudctl case save -t 1 --case https://github.com/IBM/cloud-pak/raw/master/repo/case/ibm-cp-security-1.0.19.tgz --outputdir $HOME/cp4s_cli_install/ && tar -xf $HOME/cp4s_cli_install/ibm-cp-security-1.0.19.tgz
    ```
    {: codeblock}
2. Run the following command to remove IBM Cloud Pak® foundational services:
    ```bash
    cloudctl case launch -t 1 --case ibm-cp-security --namespace ibm-common-services --inventory installProduct --action uninstall-commonservices --args "--inputDir $HOME/cp4s_cli_install/" 
    ```
    {: codeblock}


## Upgrading IBM Cloud Pak® for Security
{: #upgrade}

The steps to upgrade are the same as the steps to install. The process automatically detects an older version and initiates an upgrade.

For information about working with your Cloud Pak®, see [IBM Documentation](https://www.ibm.com/support/knowledgecenter/SSTDPP_1.7.0){: external}.

## Rolling back to a previous version of IBM Cloud Pak® for Security
{: #rollback}

1. Uninstall IBM Cloud Pak® for Security from the console by following the steps described in the [uninstall section](#uninstall). If a backup PVC existed prior to an upgrade attempt, the PVC cp4s-backup-pv-claim will be moved to the `kube-system` namespace.

2. Reinstall a previous version of IBM Cloud Pak® for Security by following install steps 1 to 5 in this [getting started](#prereqs) document and select the IBM Cloud Pak® for Security to install. If a backup PVC existed prior to the rollback installation, the PVC cp4s-backup-pv-claim will be restored from `kube-system` to `<cp4s-namespace>`.

3. Reconfigure LDAP to add or recreate any users that existed before the upgrade. For more information, see instructions based on the installed version.
    * [1.6.0.X instructions](https://www.ibm.com/docs/en/cloud-paks/cp-security/1.6.0?topic=postinstallation-configuring-ldap-authentication).
    * [1.7.0.0/1.7.1.0 instructions](https://www.ibm.com/docs/en/cloud-paks/cp-security/1.7.0?topic=only-configuring-ldap-authentication).

4. If a backup was completed before the upgrade process, you can restore the backup. For more information, see instructions based on the installed version.
    * [1.6.0.X instructions](https://www.ibm.com/docs/en/cloud-paks/cp-security/1.6.0?topic=administering-backup-restore).
    * [1.7.0.0/1.7.1.0 instructions](https://www.ibm.com/docs/en/cloud-paks/cp-security/1.7.0?topic=administering-backup-restore-premises-only).

3. Reconfigure LDAP to add or recreate any users that existed before the upgrade. For more information, see [here](https://www.ibm.com/support/knowledgecenter/SSTDPP_1.6.0/platform/docs/security-pak/ldap-connect.html).

4. If a backup was completed before the upgrade process, you can restore the backup. For more information, see [here](https://www.ibm.com/support/knowledgecenter/en/SSTDPP_1.6.0/platform/docs/scp-core/backup-intro.html).
