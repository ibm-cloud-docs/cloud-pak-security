---


copyright:
  years: 2020, 2023
lastupdated: "2023-10-23"

keywords: Cloud Pak® for Security, Install

subcollection: cloud-pak-security


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

For more information, see [IBM Documentation](https://www.ibm.com/docs/en/cp-security/1.10?topic=solution-overview){: external}.

## Purchasing a license
{: #license-entitlement}

Before you can install IBM Cloud Pak® for Security, you must purchase a license. Purchase a license, also known as an entitlement, through [IBM Passport Advantage](https://www.ibm.com/software/passportadvantage/index.html){: external}.

For more information, see [Part numbers and entitlement](https://www.ibm.com/docs/en/cp-security/1.10?topic=planning-qradar-suite-software-part-numbers-entitlement){: external}.

## Before you begin
{: #prereqs}

<!-- Before you begin prereqs: REQUIRED
Include a prerequisites sections for any prerequisites to be met. Use H3s for each applicable section.
Example: -->

Review the prerequisites so that you can successfully install the IBM Cloud Pak® for Security.

* A [Red Hat OpenShift](https://cloud.ibm.com/kubernetes/catalog/about?platformType=openshift) cluster on IBM Cloud with version 4.12.X or 4.14.X.

* The Red Hat OpenShift cluster needs to have internet access during the deployment time of IBM Cloud Pak® for Security.

* Administrator access to the Kubernetes cluster for both platform and service access policies. For more information, see [Assigning cluster access](https://cloud.ibm.com/docs/containers?topic=containers-users#add_users).

* Install the OpenShift Serverless operator and Knative Serving component using the steps [here](#openshift-serverless).

* You can install IBM Cloud Pak® for Security as a subdomain of your IBM Cloud OpenShift cluster by not specifying a `domain` while configuring your deployment. If you choose this method, Cloud Pak® for Security uses the Transport Layer Security (TLS) certificates from your IBM Cloud OpenShift cluster and the ingress subdomain is used to access IBM Cloud Pak® for Security or you can use a Fully Qualified Domain Name (FQDN) for Cloud Pak® for Security with a valid TLS certificate and certificate key. You can use the TLS certificates from your IBM Cloud® OpenShift cluster. For more information, see [Domain name and TLS certificate](https://www.ibm.com/docs/en/cp-security/1.10?topic=planning-domain-name-tls-certificates){: external}.

### Install OpenShift Serverless
{: #openshift-serverless}

1. Install OpenShift Serverless operator and ensure it is running. OpenShift Serverless is installed through the OpenShift Serverless Operator. Login to the OpenShift web console and follow the steps outlined in the [Red Hat Openshift documentation](https://docs.openshift.com/serverless/1.31/install/install-serverless-operator.html#serverless-install-web-console_install-serverless-operator).

2. Install the Knative Serving component.
    1. In the OpenShift web console, click the `+` button located in the top right of the screen and paste the following content in the YAML dialog box:
        ```yaml
        apiVersion: operator.knative.dev/v1beta1
        kind: KnativeServing
        metadata:
            name: knative-serving
            namespace: knative-serving
        spec:
            high-availability:
                replicas: 2
        ```

    2. Click on the `Create` button to start the installation of Knative Serving component.

    3. Check the conditions in the bottom of `Knative Serving` overview page and ensure that all the status are stating `True`.

### Minimum hardware requirements
{: #required-capacity}

<!-- Capacity section: REQUIRED.
All Cloud Paks specify the minimum cluster requirements. List these here so a customer can ensure to have a cluster that meets the minimum capacity. -->

| Node type | Number of nodes | CPU | RAM | Storage |
| --------- | ----------- | ----------- | ----------- | ------- |
| Worker | 3 | 16 cores | 64 GB | 120 GB |
{: caption="Table 1. Resource requirements for Cloud Pak for Security" caption-side="top"}

**Important:** The hardware requirements is validated automatically by the IBM Cloud catalog prior to the deployment.

### Minimum storage requirements
{: #min-storage-reqs}

The system disk requirements do not include the persistent storage requirements. The persistent storage requirement for IBM Cloud Pak® for Security is 3.5 TB. For more information, see [Storage requirements](https://www.ibm.com/docs/en/cp-security/1.10?topic=planning-storage-requirements){: external}.


## Step 1. Finding the Cloud Pak in the IBM Cloud Catalog
{: #catalog}

<!-- Catalog discovery: REQUIRED
Describe how to find the Cloud Pak in the catalog-->

Go to the [IBM Cloud Catalog](https://cloud.ibm.com/catalog), and select the **Cloud Paks** filter. Then, select the **IBM Cloud Pak® for Security** tile.

## Step 2. Configuring the installation
{: #configure}

1. Select the latest IBM Cloud Pak® for Security version for the installation.

2. Create or select a [RedHat OpenShift 4.12.X or 4.14.X cluster](https://cloud.ibm.com/kubernetes/catalog/about?platformType=openshift) for your installation.

3. Create or select a Project or Namespace.

4. Configure your workspace.

5. Set your deployment values as outlined in the following tables.
    | Required values | Description | Default |
    | --------- | ----------- | ----------- |
    | adminUser | The user that is to be assigned as an `Administrator` in the default Cloud Pak for Security account after installation. The `Administrator` user must exist in an Lightweight Directory Access Protocol (LDAP) directory that you will setup in the post installation task [LDAP connection](https://www.ibm.com/docs/en/cp-security/1.10?topic=providers-configuring-ldap-authentication){: external} section; or is a user that is added and authenticated using the IBM Cloud account in which the cluster was created. |
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
    | roksAuthentication | Enable ROKS Authentication. For more details, see [Configuring OpenShift authentication on IBM Cloud](https://www.ibm.com/docs/en/cp-security/1.10?topic=providers-configuring-roks-authentication){: external}. | false |
    | deployDRC | Deploy Detection and Response Center (Beta) application. Optional when deploying Cloud Pak for Security. See more details in [Detection and Response Center (Beta)](https://www.ibm.com/docs/en/cp-security/1.10?topic=organization-detection-response-center){: external}. | true |
    | deployRiskManager | Deploy Risk Manager application. Optional when deploying Cloud Pak for Security. See more details in [Risk Manager](https://www.ibm.com/docs/en/cp-security/1.10?topic=organization-risk-manager){: external}. | true |
    | deployThreatInvestigator | Deploy Threat Investigator application. Optional when deploying Cloud Pak for Security. See more details in [Threat Investigator](https://www.ibm.com/docs/en/cp-security/1.10?topic=organization-investigating-cases){: external}. | true |
    {: caption="Table 3. Optional deployment parameters for Cloud Pak for Security" caption-side="top"}
  
    For more information about certificates, see [Domain name and TLS certificate](https://www.ibm.com/docs/en/cp-security/1.10?topic=planning-domain-name-tls-certificates){: external}.  

6. Ensure that you have acquired a license for the IBM Cloud Pak® for Security deployment.

7. Confirm that you have read and agreed to the license.

## Step 3. Install your IBM Cloud Pak® for Security
{: #install}

When all the required parameters are set, click **Install**.

## Step 4. Monitor your installation in the workspace
{: #workspace}

From this stage, the installation will take approximately 1.5 hours to complete. After you start the installation, you are brought to the Schematics workspace for your Cloud Pak. You can track progress by viewing the logs. Go to the **Activity** tab, and click **View logs**.

To further track the installation, you can monitor the status of IBM Cloud Pak® for Security Threat Management:
1. Log in to the OpenShift web console and ensure you are in the Administrator view.
2. Go to **Operators** > **Installed Operators** and ensure that the **Project** is set to the namespace where IBM Cloud Pak® for Security was installed.
3. In the list of installed operators, click **IBM Cloud Pak for Security**.
4. On the **Threat Management** tab, select the **threatmgmt** instance.
5. On the Details page, the following message is displayed in the **Conditions** section when installation is complete.
   
   ```bash
   Cloudpak for Security Deployment is successful
   ``` 
   The installation is complete when you see the `Cloudpak for Security Deployment is successful` message.

## Step 5. Retrieve foundational services login details
{: #password}

Use the following commands to retrieve IBM Cloud Pak foundational services hostname, default username, and password:

* Hostname:

    ```bash
    oc -n ibm-common-services get route | grep cp-console | awk '{print $2}'
    ```
    {: codeblock}

* Username:

    ```bash
    oc -n ibm-common-services get secret platform-auth-idp-credentials -o jsonpath='{.data.admin_username}' | base64 --decode
    ```
    {: codeblock}

* Password:

    ```bash
    oc -n ibm-common-services get secret platform-auth-idp-credentials -o jsonpath='{.data.admin_password}' | base64 --decode
    ```
    {: codeblock}

    These login details are required to access foundational services and configure your LDAP directory.

## Next steps
{: #next-steps}

1. If the `adminUser` you provided is a user ID that you added and authenticated by using the IBM Cloud account that is associated with the cluster and `roksAuthentication` was enabled, go to step 2. Otherwise, [Configure LDAP authentication](https://www.ibm.com/docs/en/cp-security/1.10?topic=providers-configuring-ldap-authentication){: external} and ensure that the `adminUser` that you provided exists in the LDAP directory.

2. Log in to Cloud Pak® for Security using the domain and the `adminUser` that you provided during installation. The `domain`, also known as `application URL`, can be retrieved by running the following command:
    ```bash
    oc get route isc-route-default --no-headers -n <CP4S_NAMESPACE> | awk '{print $2}'
    ```
    {: codeblock}

    Select `Enterprise LDAP` in the login screen if you are logging in using an LDAP you connected to Foundational Services, otherwise use `OpenShift Authentication` if it is enabled.

3. [Add users to Cloud Pak® for Security](https://www.ibm.com/docs/en/cp-security/1.10?topic=administering-user-access-roles-permissions){: external}.

4. [Configure data sources](https://www.ibm.com/docs/en/cp-security/1.10?topic=connections-universal-data-insights-connectors){: external}.

## Uninstalling the IBM Cloud Pak® for Security
{: #uninstall}

Uninstalling the IBM Cloud Pak® for Security from the console:

1. Go to the workspace where you installed IBM Cloud Pak® for Security.

2. On the workspace toolbar, click the **Actions** button.

3. To uninstall, click **Destroy**.

4. To confirm, enter the name of the workspace to uninstall. To uninstall, click **Destroy**.

5. Wait for the Cloud Pak to finish uninstalling.

6. To verify that the IBM Cloud Pak® for Security is uninstalled, access the OpenShift web console and verify that the components that are related to the IBM Cloud Pak® for Security, such as any related pods, are no longer installed.


**Important note:** The uninstall only removes the instance IBM Cloud Pak® for Security Threat Management CR and does not terminate the namespace. It also does not remove the IBM Cloud Pak® Foundational Services that are installed in the cluster. If you want to remove all the IBM Cloud Pak® for Security resources and terminate the namespace or remove the IBM Cloud Pak® Foundational Services, see [Uninstalling IBM Cloud Pak® for Security using CLI](https://www.ibm.com/docs/en/cp-security/1.10?topic=software-uninstalling-qradar-suite-by-using-cli){: external}. 


## Upgrading IBM Cloud Pak® for Security
{: #upgrade}

If your approval strategy is set to **Automatic**, the IBM Cloud Pak® for Security operator upgrades automatically when new compatible versions are available. For more information, see [Approval Strategy](https://www.ibm.com/docs/en/cp-security/1.10?topic=administering-approval-strategy){: external}. 

To upgrade IBM Cloud Pak® for Security when your approval strategy is set to **Manual**, see [Upgrading to a later 1.10 release when your approval strategy is set to Manual](https://www.ibm.com/docs/en/cp-security/1.10?topic=installing-upgrading-qradar-suite-software#upgrade_manual){: external}.


<!-- DRAFTED: Rollback not supported currently (drafted for future use)
## Rolling back to a previous version of IBM Cloud Pak® for Security
{: #rollback}

1. Uninstall IBM Cloud Pak® for Security completely using the CLI by following the steps described in [Uninstalling IBM Cloud Pak® for Security using CLI](https://www.ibm.com/docs/en/cp-security/1.10?topic=software-uninstalling-qradar-suite-by-using-cli){: external}.

2. Reinstall a previous version of IBM Cloud Pak® for Security and verify the installation. For more information, see [Installing IBM Cloud Pak® for Security using CLI](https://www.ibm.com/docs/en/cp-security/1.10?topic=installing-qradar-suite-software-by-using-red-hat-openshift-cli){: external}.

3. Reconfigure LDAP to add or recreate any users that existed before the upgrade. For more information, see [Configure LDAP](https://www.ibm.com/docs/en/cp-security/1.10?topic=providers-configuring-ldap-authentication){: external}.

4. If a backup was completed before the upgrade process, you can restore the backup. For more information, see [Backup and Restore](https://www.ibm.com/docs/en/cp-security/1.10?topic=administering-backup-restore){: external}. -->
