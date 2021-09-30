---


copyright:
  years: 2020,2021
lastupdated: "2021-09-30"

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
{: shortdesc}

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
 - IBM® Detection and Response Center (Beta) provides a unified overview of your organization’s security posture through use cases from different security tools and platforms, saving you hours of gathering the same insights by using individual tools.
    
For more information, see [IBM Documentation](https://www.ibm.com/docs/en/SSTDPP_1.8/docs/scp-core/overview.html)

## Purchasing a license
{: #license-entitlement}

Before you can install IBM Cloud Pak® for Security, you must purchase a license. Purchase a license, also known as an entitlement, through [IBM Passport Advantage](https://www.ibm.com/software/passportadvantage/index.html){: external}.

For more information, see [Licensing and entitlement](https://www.ibm.com/docs/en/SSTDPP_1.8/docs/security-pak/app_licensereq.html){: external}.

## Before you begin
{: #prereqs}
<!-- Before you begin prereqs: REQUIRED
Include a prerequisites sections for any prerequisites to be met. Use H3s for each applicable section.
Example: -->

Review the prerequisites so that you can successfully install the IBM Cloud Pak® for Security.

* A single-zone cluster [Red Hat OpenShift on IBM Cloud Version 4.6.X or 4.7.X](https://cloud.ibm.com/kubernetes/catalog/about?platformType=openshift). 

* Administrator access to the Kubernetes cluster for both platform and service access policies. For more information, see [Assigning cluster access](https://cloud.ibm.com/docs/containers?topic=containers-users#access_policies).

* You can install IBM Cloud Pak® for Security as a subdomain of your IBM Cloud OpenShift cluster by not specifying a `domain` while configuring your deployment. If you choose this method, Cloud Pak® for Security uses the Transport Layer Security (TLS) certificates from your IBM Cloud OpenShift cluster and the ingress subdomain is used to access IBM Cloud Pak® for Security.

* A valid TLS certificate and certificate key for the Cloud Pak® for Security Fully Qualified Domain Name (FQDN). You can use the TLS certificates from your IBM Cloud® OpenShift cluster. For more information, see [Domain name and TLS certificate](https://www.ibm.com/docs/en/SSTDPP_1.8/docs/security-pak/tls_certs.html){: external}.



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

The system disk requirements do not include the persistent storage requirements. The persistent storage requirement for IBM Cloud Pak® for Security is 3.5 TB. For more information, see [persistent storage requirements](https://www.ibm.com/docs/en/SSTDPP_1.8/docs/security-pak/persistent_storage.html){: external}.


## Step 1. Finding the Cloud Pak in the IBM Cloud Catalog
{: #catalog}

<!-- Catalog discovery: REQUIRED
Describe how to find the Cloud Pak in the catalog-->

Go to the [IBM Cloud Catalog](https://cloud.ibm.com/catalog), and select the **Cloud Paks** filter. Then, select the **IBM Cloud Pak® for Security** tile.

## Step 2. Configuring the installation
{: #configure}

1. Select the IBM Cloud Pak® for Security 1.8.0.0 version to install.

2. Create or select a [RedHat OpenShift 4.6.X or 4.7.X cluster](https://cloud.ibm.com/kubernetes/catalog/about?platformType=openshift) for your installation.

3. Create or select a Project or Namespace.

4. Configure your workspace.

5. Set your deployment values as outlined in the following tables. 
    | Required values | Description | Default |
    | --------- | ----------- | ----------- |
    | adminUser | The user that is to be assigned as an `Administrator` in the default Cloud Pak for Security account after installation. The `Administrator` user must exist in an Lightweight Directory Access Protocol (LDAP) directory that you will setup in the post installation task [LDAP connection](https://www.ibm.com/docs/en/SSTDPP_1.8/docs/security-pak/ldap-connect.html) section; or is a user that is added and authenticated using the IBM Cloud account in which the cluster was created. |
    {: caption="Table 2. Required deployment parameters for Cloud Pak for Security" caption-side="top"}

    **Note:** The user that you provide as `adminUser` must be the admin for the LDAP directory with an email address in the LDAP directory. Take note of the user that you provide as that user will be required as the initial user to log in to IBM Cloud Pak® for Security.

    | Optional values  | Description | Default |
    | --------- | ----------- | ----------- |
    | domain | The Fully Qualified Domain Name (FQDN) created for Cloud Pak for Security. When the domain is not specified, it will be generated as `cp4s.<cluster_ingress_subdomain>`. |  | 
    | domainCertificate | TLS certificate associated to the IBM Cloud Pak&reg; for Security application domain. If the `domain` is not specified, OpenShift cluster certificates will be used. |  | 
    | domainCertificateKey | TLS key associated to the IBM Cloud Pak&reg; for Security application domain. If the `domain` is not specified, OpenShift cluster certificates will be used. | | 
    | customCA | Custom TLS certificate associated to the IBM Cloud Pak&reg; for Security application domain. |  |
    | storageClass | The provisioned block or file storage class to be used for creating all the PVCs required by IBM Cloud Pak&reg; for Security. When it is not specified, the default storage class in the cluster will be used. |  
    | backupStorageClass | Storage class used for creating the backup PVC. If this value is not set, IBM Cloud Pak&reg; for Security will use the same value set in `storageClass` parameter. |  |
    | backupStorageSize | Override the default backup storage PVC size. | 500Gi |
    | imagePullPolicy | Image pull policy for the containers. | IfNotPresent |
    | roksAuthentication | Enable ROKS Authentication. For more details, see https://www.ibm.com/docs/en/cpfs?topic=types-delegating-authentication-openshift. | false |
    | deployDRC | Deploy Detection and Response Center (Beta) application. Optional when deploying Cloud Pak for Security. See more details in (https://ibm.biz/Bdf8VX). | true |
    | deployRiskManager | Deploy Risk Manager application. Optional when deploying Cloud Pak for Security. See more details in (https://ibm.biz/Bdf8VX). | true |
    | deployThreatInvestigator | Deploy Threat Investigator application. Optional when deploying Cloud Pak for Security. See more details in (https://ibm.biz/Bdf8VX). | true |
    {: caption="Table 3. Optional deployment parameters for Cloud Pak for Security" caption-side="top"}
  
    For more information about certificates, see [Domain name and TLS certificate](https://www.ibm.com/docs/en/SSTDPP_1.8/docs/security-pak/tls_certs.html){: external}.  

6. Ensure that you have acquired a license for the IBM Cloud Pak® for Security deployment.

7. Confirm that you have read and agreed to the license.  

## Step 3. Install your IBM Cloud Pak® for Security
{: #install}

When all the required parameters are set, click **Install**.

## Step 4. Monitor your installation in the workspace
{: #workspace}

From this stage, the installation will take approximately 1.5 hours to complete which includes the installation of IBM Cloud Pak foundational services. After you start the installation, you are brought to the Schematics workspace for your Cloud Pak. You can track progress by viewing the logs. Go to the **Activity** tab, and click **View logs**.

To further track the installation, you can run the following command once you are logged into your cluster using OpenShift CLI:
   ```bash
   oc get CP4SThreatManagement threatmgmt -n <CP4S_NAMESPACE> -o jsonpath='{.status.conditions}'
   ```
{: codeblock}

The installation is complete when you see the message `Cloudpak for Security Deployment is successful`.

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

1. If the `adminUser` you provided is a user ID that you added and authenticated by using the IBM Cloud account that is associated with the cluster and `OpenShiftAuthentication` was enabled, go to step 2. Otherwise, [Configure LDAP authentication](https://www.ibm.com/docs/en/SSTDPP_1.8/docs/security-pak/ldap-connect.html){: external} and ensure that the `adminUser` that you provided exists in the LDAP directory. and ensure that the `adminUser` that you provided exists in the LDAP directory.

2. Log in to Cloud Pak® for Security using the domain and the `adminUser` that you provided during installation. The `domain`, also known as `application URL`, can be retrieved by running the following command:
    ```bash
    oc get route isc-route-default --no-headers -n <CP4S_NAMESPACE> | awk '{print $2}'
    ```
    {: codeblock}

    Select `Enterprise LDAP` in the login screen if you are logging in using an LDAP you connected to Foundational Services, otherwise use `OpenShift Authentication` if it is enabled.

3. [Add users to Cloud Pak® for Security](https://www.ibm.com/docs/en/SSTDPP_1.8/docs/scp-core/users.html){: external}.

4. Install the [IBM® Security Orchestration & Automation license](https://www.ibm.com/docs/en/SSTDPP_1.8/docs/security-pak/license_UI.html){: external}.
If you choose Orchestration & Automation as part of your Cloud Pak® for Security bundle, you must install your Orchestration & Automation license to access the complete orchestration and automation capabilities that are provided by Orchestration & Automation.

5. [Configure data sources](https://www.ibm.com/docs/en/SSTDPP_1.8/docs/scp-core/data-sources.html){: external}.

## Uninstalling the IBM Cloud Pak® for Security
{: #uninstall}

Uninstalling the IBM Cloud Pak® for Security from the console:

1. Go to the workspace where you installed IBM Cloud Pak® for Security.

2. On the workspace toolbar, click the **Actions** button. 

3. To uninstall, click **Destroy**.

3. To confirm, enter the name of the workspace to uninstall. To uninstall, click **Destroy**.

4. Wait for the Cloud Pak to finish uninstalling.

5. To verify that the IBM Cloud Pak® for Security is uninstalled, access the OpenShift web console and verify that the components that are related to the IBM Cloud Pak® for Security, such as any related pods, are no longer installed.

**Important notes:** 
* The uninstall only removes the instance IBM Cloud Pak® for Security Threat Management CR and does not terminate the namespace. If you want to remove the all the resources and terminate the namespace, see [Uninstalling IBM Cloud Pak® for Security using CLI](https://www.ibm.com/docs/en/SSTDPP_1.8/docs/security-pak/uninstallCP4S_OpenshiftCLI.html). 
* The uninstall also does not remove the IBM Cloud Pak® Foundational Services that are installed in the cluster. To manually remove the foundational services, see [Uninstalling Foundational Services](#uninstall-cs).

## (Optional) Uninstalling Foundational Services
{: #uninstall-cs}

To uninstall the IBM Cloud Pak® Foundational Services that are installed in the cluster, complete the following procedure. This procedure requires you to have the `oc` and `cloudctl` CLI tools installed in your local machine. To install the required CLI tools, follow the steps in [Installing developer tools](https://www.ibm.com/docs/en/SSTDPP_1.8/docs/security-pak/cscli_tool_guide.html){: external}.
1. Download and extract the IBM Cloud Pak® for Security archive file:

    1. Create a directory that will serve as your working directory which will include all the files needed for the install. **Important:** If you already have the `cp4s_install` directory in your home directory, before you run the command you must rename or delete the existing directory.
        ```bash
        export CP4S_DIR=$HOME/cp4s_install
        mkdir $CP4S_DIR && cd $CP4S_DIR
        ```
        {: codeblock}

    2. Download and extract the archive file for IBM Cloud Pak® for Security within the created directory:
        ```bash
        cloudctl case save \
        --repo https://github.com/IBM/cloud-pak/raw/master/repo/case \
        --case ibm-cp-security \
        --version 1.0.20 \
        --outputdir $CP4S_DIR \
        && tar -xf $CP4S_DIR/ibm-cp-security-1.0.20.tgz
        ```
        {: codeblock}
        
2. Login to the cluster.

    Ensure that you are logged in to the cluster by using either of the following `oc login` commands:

    * Using username and password:
        ```bash
        oc login <OPENSHIFT_URL> -u <USERNAME> -p <PASSWORD>
        ```
        {: codeblock}

    * Using a token:
        ```bash
        oc login --token=<TOKEN> --server=<OPENSHIFT_URL>
        ```
        {: codeblock}


3. Run the following command to remove IBM Cloud Pak® foundational services:
    ```bash
    cloudctl case launch \
        --case ibm-cp-security \
        --namespace ibm-common-services \
        --inventory ibmSecurityOperatorSetup \
        --action uninstall-foundationalservices \
        --args "--inputDir $CP4S_DIR"
    ```
    {: codeblock}


## Upgrading IBM Cloud Pak® for Security
{: #upgrade}

The steps to upgrade are the same as the steps to install. The process automatically detects an older version and initiates an upgrade. Ensure that when filling in the parameters, the following parameters matches what you used to have in IBM Cloud Pak® for Security 1.7.2.0:

* `namespace` - Provide the namespace where IBM Cloud Pak® for Security 1.7.2.0 was installed.

* `adminUser` - The admin user ID set during the IBM Cloud Pak® for Security 1.7.2.0 installation. You can verify the value by running the following command:
  ```bash
    oc get deploy isc-entitlements -o yaml -n <CP4S_NAMESPACE> | grep "name: ADMIN_USER_ID" -A1
  ```
  {: codeblock}

* `domain` - The current domain being used by {{site.data.keyword.isc}} can be retrieved by running the following command:
  ```bash
    oc get route isc-route-default -o jsonpath='{.spec.host}' -n <CP4S_NAMESPACE>
  ```
  {: codeblock}

* `storageClass` - Set the storage class to the same storage class being used in IBM Cloud Pak® for Security 1.7.2.0 which should be default storage class. You can run the following command to verify the default storage class in the cluster:
  ```bash
    oc get sc
  ```
  {: codeblock}

* `roksAuthentication` - Set this to the same value you used in the `cp4sOpenshiftAuthentication` parameter when installing IBM Cloud Pak® for Security 1.7.2.0. Verify the value that you used by running the following command:
    ```bash
    oc get cm platform-auth-idp -n ibm-common-services -o jsonpath='{.data.ROKS_ENABLED}'
    ```
    {: codeblock}

For information about upgrading your IBM Cloud Pak® for Security, see [Upgrading](https://www.ibm.com/docs/en/SSTDPP_1.8/docs/security-pak/upgrading.html){: external}.

## Rolling back to a previous version of IBM Cloud Pak® for Security
{: #rollback}

1. Uninstall IBM Cloud Pak® for Security completely using the CLI by following the steps described in [Uninstalling IBM Cloud Pak® for Security using CLI](https://www.ibm.com/docs/en/SSTDPP_1.8/docs/security-pak/uninstallCP4S_OpenshiftCLI.html){: external}.

2. Reinstall a previous version of IBM Cloud Pak® for Security by following install steps 1 to 5 in this [Getting started](#prereqs) document and select the 1.7.2.0 IBM Cloud Pak® for Security to install.

3. Reconfigure LDAP to add or recreate any users that existed before the upgrade. For more information, see [Configure LDAP](https://www.ibm.com/docs/en/SSTDPP_1.8/docs/security-pak/ldap-connect.html){: external}.

4. If a backup was completed before the upgrade process, you can restore the backup. For more information, see [Backup and Restore](https://www.ibm.com/docs/en/SSTDPP_1.8/docs/scp-core/backup-intro.html).
