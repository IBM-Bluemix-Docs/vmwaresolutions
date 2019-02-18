---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-05"

---

# Fully distributed

Additional base virtual machines (VMs) and scale-out VMs are added according to the number of assets and data retention requirements.

Table 1. Base - user interface

|Parameter	|Value|
|---|---|
|Type	|Base|
|VM qty	|2|
|vCPU	|2|
|RAM	|6 GB|
|Disk	|60 GB|
|OS	|CentOS 7|
|Installed Application Components	|UI|

Table 2. Base - applications and plug-ins

|Parameter	|Value|
|---|---|
|Type	|Base|
|VM qty	|2|
|vCPU	|8|
|RAM	|16 GB|
|Disk	|500 GB|
|OS	|CentOS 7|
|Installed Application Components	|App, Plugins|

Table 3. Base - central collector

|Parameter	|Value |
|---|---|
|Type	|Base |
|VM qty	|3 |
|vCPU	|8 |
|RAM	|16 GB |
|Disk	|500 GB |
|OS	|CentOS 7 |
|Installed Application Components	|Central Collector (Cluster) |

Table 4. Base - relational database

|Parameter	|Value |
|---|---|
|Type	|Base |
|VM qty	|2 |
|vCPU	|8 |
|RAM	|16 GB |
|Disk	|1 TB |
|OS	C|entOS 7 |
|Installed Application Components	|Relational Datastore (Primary / Secondary) |

Table 5. Base - messaging datastore

|Parameter	|Value |
|---|---|
|Type	|Base |
|VM qty	|3 |
|vCPU	|8 |
|RAM	|16 GB |
|Disk	|1 TB |
|OS	|CentOS 7 |
|Installed Application Components	|Messaging Datastore (Cluster) |

Table 6. Base - index datastore (master nodes)

|Parameter	|Value |
|---|---|
|Type	|Base |
|VM qty	|3 |
|vCPU	|8 |
|RAM	|16 GB |
|Disk	|1 TB |
|OS	|CentOS 7 |
|Installed Application Components	|Index Datastore (Master Nodes) |

Table 7. Database - index datastore (data nodes)

|Parameter	|Value |
|---|---|
|Type	|Base |
|VM qty	|5 |
|vCPU	|8 |
|RAM	|16 GB |
|Disk	|4 TB |
|OS	|CentOS 7 |
|Installed Application Components	|Index Datastore (Data Nodes) |

The scale-out VM details are described in the following table.

Table 8. Scale-out - data nodes

|Parameter	|Value |
|---|---|
|Type	|Scale-out |
|VM qty	28 |
|vCPU	|8 |
|RAM	|16 GB |
|Disk	|4 TB |
|OS	|CentOS 7 |
|Installed Application Components	|Data Nodes (scale-out) |

The Remote Collector VM details are shown in the following table.

Table 9. Remote collector

|Parameter	|Value |
|---|---|
|VM qty	|As required |
|vCPU	|8 |
|RAM	|8 GB |
|Disk	|1 TB |
|OS	|CentOS 7 |
|Installed Application Components	|Remote Collector |

## Related Links

* [VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcenter-server-on-ibm-cloud-with-hybridity-bundle-overview)
