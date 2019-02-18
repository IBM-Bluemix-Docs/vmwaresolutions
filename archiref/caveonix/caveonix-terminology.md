---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-01"

---

# Glossary of Caveonix terms
This glossary provides some descriptions for terms that are unassociated with the Caveonix RiskForesight solution:

-	**NIST Special Publication 800-53:** A Risk Management Framework that address security control.
-	**Security Content Automation Protocol (SCAP):** A method for using specific standards to enable the automated vulnerability management, measurement, and policy compliance evaluation of systems deployed in an organization. Checklists standardize and enable automation of the linkage between computer security configurations and the NIST Special Publication 800-53 controls framework.
  - The National Vulnerability Database (NVD) is the US government content repository for SCAP.
  -	SCAP allows security administrators to scan computers, software, and other devices based on a predetermined security baseline to determine whether the configuration and software patches are implemented to the standard that they are being compared to.
  SCAP components are as follows:
  -	Common Vulnerabilities and Exposures (CVE) - A list of publicly known cybersecurity vulnerabilities.
  -	Common Configuration Enumeration (CCE) – A list of security-related system configuration issues.
  -	Common Platform Enumeration (CPE) - A structured naming scheme for information technology systems, software, and packages.
  -	Common Weakness Enumeration (CWE) – A list of common software security weaknesses.
  -	Common Vulnerability Scoring System (CVSS) - Provides a way to capture the principal characteristics of a vulnerability and produce a numerical score reflecting its severity.
  -	Extensible Configuration Checklist Description Format (XCCDF) - A specification language for writing security checklists, benchmarks, and related kinds of documents. An XCCDF document represents a structured collection of security configuration rules for some set of target systems.
  -	Open Vulnerability and Assessment Language (OVAL) – A language that is used to encode system details, and an assortment of content repositories. The language standardizes the three main steps of the assessment process:
      - Representing configuration information of systems for testing.
      -	Analyzing the system (vulnerability, configuration, and patch state)
      -	Reporting the results of this assessment.
-	**Security Technical Implementation Guide (STIG):** A cybersecurity methodology for standardizing security protocols within networks, servers, computers, and logical designs to enhance overall security. These guides, when implemented, enhance security for software, hardware, physical and logical architectures to further reduce vulnerabilities.
-	**Service Provider:** The top-level organization.
-	Cloud Provider - Provides the infrastructure that the software defined cloud operates on. RiskForesight can be configured for multiple Cloud Providers.
-	**Organizations:** Tenant organizations and sub-organizations of the Service Provider. If the Asset Repository is vCenter, the Organization / Tenant List must be created manually.
-	**Roles:** Pre-configured Roles and Service Provider created Roles. Preconfigured roles are not editable by the Service Provider.
-	**Organization Users:** Users of the Tenant Organizations and Sub-Organizations.
-	**Asset Repository:** An integration point that enables RiskForesight to synchronize the current asset across the CSP management zone and customer zone. The current version of RiskForesight supports the synchronization for VMware vCloud Director and vCenter Servers. It also supports data collection from VMware NSX Manager. Assets	are collected from the Asset Repository. The Service Provider assigns Assets that are collected from vCenter to Tenant Organizations and Sub-Organizations of the Service Provider. An Asset can be assigned only to one Organization.
-	**Remote Access:** Provides end machine credentials to enable scans for vulnerability and compliance monitoring and to collect system events logs. The SP can only enable remote access for their own assets. Tenants have control over remote access from their Assets.
-	**Applications and sub applications:** A logical way to group assets. Example Application: SAP, example Sub-Applications: SAP Front End, SAP Middle Tier, SAP Back End.
-	**Locations:** Assets are uniquely grouped by Location, Cloud Provider, and Asset Repository.
-	**Environments:** A way to group Assets and Applications. Each Environment is assigned a risk factor 1 - 10. This factor is applied in the risk score calculation. Service Provider defines the Environments
-	**Tasks:** Used in RiskForesight to:
  -	Periodically synchronize the Asset Repository with RiskForesight.
  -	Perform SCAP Vulnerability and Compliance scans.
  -	Collect network flows and other information that uses NSX scans.
  -	Collect information about the software that runs on monitored Assets.
  -	Collect syslog and system events for Assets.
-	**Task Types:** The following tasks are supported:
  -	**VMware vCenter Scan:** Collects Assets from vCenter.
	- **VMware VCD Scan:** Collects Assets from VCD.
  -	**VMware NSX Scan:** Collects network information and network flow from NSX Manager.
  - **SCAP Scan:** This scan type is used for scanning workloads for Compliance and Cyber Risk. This scan is based on the SCAP (Security Content Automation Protocol). Future releases are planned to support custom content in the OVAL format.
  - **Software Scan:** This scan collects the software inventory that is installed on the target workload under management. This inventory is then available for search through the search option in the UI top bar.
  - **LogExtract:** This scan supports log collection from Windows and Linux workloads. This is used for forensics purposes and ingested through machine learning to produce useful information.
  - **AMQP Task:** This AMQP task is used for collecting live events from the VCD to enable real-time sync. RiskForesight consumes Asset add, delete, and update events and acts on these events. For example, if a new asset gets added and RiskForesight received that notification through AMQP then it updates the database immediately and starts the Compliance and Cyber Risk scan.
  - **VMware Infrastructure Scan:** This scan carries out an infrastructure scan of the VMware Assets.
  -	**VMware Vulnerability Scan:** This scan carries out a Vulnerability scan of the VMware Assets.
-	**Compliance Regime:** Available through license; NIST, NESA, PCI, ISO, HIPAA, GDPR, Custom, FFIEC, FedRAMP Low, FedRAMP Moderate, FedRAMP High
-	**Policy Manager:** The Policy Manager serves policy creation function for an Organization based on the machine learning output. Caveonix provides by default three types of machine learning jobs per Organization. Those are non-editable and additional jobs are not supported yet. Those will be available in a future release. The currently supported types of machine learning jobs are:
  -	Caveo Logs
  -	Caveo Networks
  -	Caveo Scan
-	**Anomaly:** Based on the anomalies that are found in the data we can configure the policies to take action based on the user-defined conditions. You can select the job type and configure Boolean conditions for the anomaly score and define action when condition is true. For example:
  -	Job: "Caveo Logs" Anomaly score is > 90 then Mark asset for quarantine and send Notification to slack Channel.
  -	Job: "Caveo Network" Anomaly score is > 95 then quarantine the asset and send email notification and also send UI notification.

### Related Links

* [VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcenter-server-on-ibm-cloud-with-hybridity-bundle-overview)
