---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-06"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# KMIP for VMware implementation and management

## Connecting the key management server

To enable vSphere encryption or vSAN encryption by using KMIP for VMware on {{site.data.keyword.cloud_notm}}, you need to complete the following tasks:

1. [Enable your account for service endpoints](/docs/services/service-endpoint?topic=services/service-endpoint-getting-started#getting-started).
2. Create an [IBM Key Protect](/docs/services/key-protect?topic=key-protect-getting-started-tutorial) instance.
3. Create a customer root key (CRK) within IBM Key Protect.
4. Create an Identity and Access Management (IAM) [service ID and API key](/docs/iam?topic=iam-serviceidapikeys) for use with KMIP for VMware. Grant this service ID platform viewer access and service write access to your Key Protect instance.
5. Create a [KMIP for VMware](/docs/services/vmwaresolutions/services?topic=vmware-solutions-ordering-kmip-for-vmware-on-ibm-cloud-instances) instance from the {{site.data.keyword.cloud_notm}} catalog.
6. Within VMware vCenter, create a key management server (KMS) cluster with two servers, one for each KMIP for VMware endpoint in your chosen region.
7. Select one of VMware&rsquo;s methods to generate or install a KMS client certificate in vCenter.
8. Export the public version of the certificate and configure it as an allowed client certificate in your KMIP for VMware instance.

## Enabling encryption

To use vSAN encryption, edit the vSAN general settings in your vCenter cluster and select the encryption check box.

The vSAN health check might issue periodic warnings that it is unable to connect to the KMS cluster from one or more of your vSphere hosts. These warnings occur because the vSAN health check connection times out too quickly. You can ignore these warnings.
{:note}

To use vSphere encryption, edit your virtual machine storage policies to require disk encryption.

## Key rotation

[Rotate your Key Protect customer root key (CRK)](/docs/services/key-protect?topic=key-protect-rotating-keys) by using the {{site.data.keyword.cloud_notm}} console or API.

For VMware vSAN encryption, rotate your VMware key&ndash;encrypting keys (KEKs) and optionally data&ndash;encrypting keys (DEKs) from the vSAN general settings in your vCenter cluster.

For VMware vSphere encryption, rotate your VMware KEKs and DEKs (optionally) by using the **Set-VMEncryptionKey** PowerShell command.

## Key revocation

You can revoke all keys in use by KMIP for VMware by deleting your chosen CRK from Key Protect.

When keys are revoked, all data that is protected by these keys and by your KMIP for VMware instance is cryptographically shredded by this method. VMware preserves some keys while an ESXi host is powered on, so you need to restart your vSphere cluster to ensure that all encrypted data is no longer in use.
{:important}

KMIP for VMware stores individual wrapped KEKs in your Key Protect instance by using names that are associated with the key IDs that are known to VMware. You can delete individual keys to revoke the encryption of individual disks or drives.

VMware does not delete keys from the KMS when a VM having encrypted disks is removed from inventory. This is to allow recovery of that VM from backup or if it is restored to inventory. If you wish to reclaim these keys and cryptographically invalidate all backups, you need to delete the keys from Key Protect after deleting your VMs.
{:note}

### Related links

* [Solution overview](/docs/services/vmwaresolutions/archiref/kmip?topic=vmware-solutions-kmip-for-vmware-overview)
* [Solution design](/docs/services/vmwaresolutions/archiref/kmip?topic=vmware-solutions-kmip-for-vmware-design)
* [IBM Key Protect](/docs/services/key-protect?topic=key-protect-getting-started-tutorial)
