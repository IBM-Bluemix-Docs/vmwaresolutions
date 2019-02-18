---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-06"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Deployment models for Caveonix RiskForesight

This section describes the deployment models for Caveonix RiskForesight along with the installation process for installing the solution.

When you select the {{site.data.keyword.vmwaresolutions_full}} RiskForesight option, you do not have to follow all the steps in the deployment as the initial ones are automated. However, for an understanding of the complete deployment and architecture, and for those who want to scale out the solution after the initial deployment, a detailed understanding is required.

The RiskForesight installation consists of the following high-level steps:

1. [Initial planning and prerequisites](/docs/services/vmwaresolutions/archiref/caveonix?topic=vmware-solutions-step-1-initial-planning-and-prerequisites) – Understanding and selecting a deployment option, configuring DNS to provide FQDN/IP resolution for the application components.
2. [Virtual machine deployment](/docs/services/vmwaresolutions/archiref/caveonix?topic=vmware-solutions-step-2-virtual-machine-deployment) – Deploying the VMs from an OVF template. The VM has installed on it all the application components.
3. [Application configuration](/docs/services/vmwaresolutions/archiref/caveonix?topic=vmware-solutions-step-3-application-configuration) – Running the Caveonix configuration script that configures the application component on each of the VMs.
4. [Application setup](/docs/services/vmwaresolutions/archiref/caveonix?topic=vmware-solutions-step-4-application-setup) – Setting up the Service Provider and a Tenant or Organization so that the application becomes accessible for the users.

The automated install, provisions one VM and configures all the application components on that VM.
{:note}

## Deployment sizing

The deployment sizing is calculated by using the following volumes.

Table 1. Volumes

|Data type	|Volume |
|---|---|
|Scans per Day	|1 |
|Scan Data (MB)	|20 |
|Log Data (MB)	|500 |
|Flow Data (MB)	|200 |
|Asset Data (MB)	|46 |
|Total Storage per Asset per Day (MB)	|766 |
|Data Replication Multiplier	|2 |
|Total Index Storage / Asset / Day (MB)	|1532 |

The Data Replication Multiplier is set to 2 as the Index store (Elastic Search) uses by default n+1 replication of the indexes.
{:note}

The number of Scaling VMs is calculated from the number of Assets and the number of days of data to index.

Table 2. Scaling VM parameters

|Number of assets	|100	|500	|5000 |
|---|---|---|---|
|Days of Data	|30	|30	|30 |
|Total Index Storage / Asset / Day (MB)	|1532	|1532	|1532 |
|Total Index Storage / Asset / 30 Days (TB)	|4	|22	|219 |
|Data Supported per Scaling Node (TB)	|0	|8	|8 |
|Scaling VMs Required	|0	|3	|27 |

The amount of storage that is required is calculated as follows:

Table 3. Storage parameters

|Number of assets	|100	|500	|5000 |
|---|---|---|---|
|Long Term Data Retention (Months)	|8	|8	|8 |
|Total Storage per Asset per Day (MB)	|766	|766	|766 |
|Days of Data	|30	|30	|30 |
|Near Term Data Retention (TB)	|7	|33	|329 |
|Long Term Data Retention (TB)	|18	|88	|877 |

From a data perspective, data is used as follows:

-	Scan data is used in Compliance Management
-	Log data is used in forensic management
-	Policy and flow data is used in risk management and flow data is only available from NSX Manager

Data Storage has three tiers:

-	Replicated
-	Near Term
-	Long Term

The following table provides a summary of the deployments:

Table 4. Summary

|Deployment model	|“all-in-one”	|Partial distributed	|Fully distributed |
|---|---|---|---|
|Number of Assets	|100	|500	|5000 |
|Online Data Generated in 30 Days (TB)	|4	|22	|219 |
|Nearline Data Retention (90 Days) (TB)	|7	|33	|329 |
|Offline Data Retention (8 Months) (TB)	|18	|88	|877 |
|Total Data Storage Retention (1 Year) (TB)	|28	|142	|1425 |
|Base VMs	|1	|1	|20 |
|Scaling VMs	|0	|3	|28 |
|Total VMs	|1	|4	|48 |

### Related Links

* [VMware vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcenter-server-on-ibm-cloud-with-hybridity-bundle-overview)
