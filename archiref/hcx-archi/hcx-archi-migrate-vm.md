---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-24"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Migrating a virtual machine

HCX enables bidirectional migration: from on-premises to the cloud, or from the cloud to the on-premises data center. HCX uses replication technology during the migration process. Replication technology is integrated in the Hybrid Cloud Gateway virtual appliance. No additional replication software needs to be installed.

## Low downtime migration

Low downtime migration uses host-based replication to move a live virtual machine from a vCenter to a virtual data center or the opposite direction. To reduce downtime, the source VM remains online during the replication and is bootstrapped on the destination ESX host after replication completes.

1. A migration request triggers the following actions:
  * Replication begins a full synchronization transfer into a VCF/VCS HCX virtual data center. The time that it takes to replicate depends on the size of the VM and available bandwidth.
  * Replication bandwidth consumption varies depending on how the workload changes blocks on the disk.
2. When full synchronization finishes, a delta synchronization occurs.
3. When the delta synchronization finishes, HCX triggers a switchover. The switchover can start immediately or scheduled until a specific time.
4. Following the switchover, the source VM is powered-off, and the migrated replica is powered on. If for some reason the VM cannot power on, the new VM is powered off (or remains powered off) and the original is powered on.
5. HCX renames the powered off original VM to avoid a naming conflict with the migrated VM and appends a binary time stamp to the original VM name.
6. If it was not specified to enable **Retain MAC**, the migrated VM obtains a new MAC address.
7. The migration is done. Hybrid Cloud Services copies the original VM to the **Migrated VMs** folder in the vSphere Templates view.

## No downtime vMotion

vMotion transfers a live virtual machine from a vSphere vCenter to a VCF/VCS Cloud. This vMotion requires a stretched network. The vMotion transfer captures the virtual machine's active memory, its execution state, its IP address, and its MAC address.

The virtual machine hardware version must be at least version 9, or cross-cloud vMotion might fail.
{:note}

## Cold migration

Cold migration uses the same data plane as cross-cloud vMotion to transfer a powered-off virtual machine over an extended network. Its IP address and MAC address are preserved. The virtual machine requirements and restrictions are the same as for vMotion.

### Migrating VMs by using the bidirectional wizard

Using the vSphere Web Client, the bidirectional migration wizard is accessible from the Hybrid Cloud Services Getting Started tab. This wizard handles all migration details, including multiple virtual machines.

From the vSphere Web Client, the bidirectional migration wizard can be accessed from the Hybrid Cloud Services Getting Started tab. This wizard handles all migration details, including multiple virtual machines.
* From vSphere to VCF/VCS Hybrid Cloud Services
* From VCF/VCS HCX Cloud to vSphere

### Checking the VMs before migration

To migrate a virtual machine, a secure connection that is maintained by the Hybrid Cloud Gateway is required, and the VM must meet the following requirements:
* The virtual machine must be powered on.
* The underlying architecture must be x86, regardless of the operating system.
* To use vMotion migration, the hardware version must be greater than 9.
* The hardware version must be less than 10.
* VMs with Raw Disk Mapping in compatibility mode can be migrated.

VMs with the following attributes are not supported for migration:
* Exceed 2 TB.
* Share VMDK files.
* Have virtual media or ISOs attached.
* Hardware version less than 9.

### Monitoring a migration

The progress of a replication-based migration can be monitored from the user interface, or from the command line. View the Task console, as described in Monitor Service Appliance Deployment, and look for the **Migrate VM** task. When the status is **Completed**, the VM is migrated and powered on.

This procedure uses an unrelated VM in the same vCenter to track the progress of a migrated VM.

1. Identify the VM to migrate, and choose an observer VM that can ping the migrating VM.
2. From the user interface, start migrating the VM, and monitor it from the Task console.
3. Using SSH, log in to the ESXi host that runs the observer VM.
4. Run the following command to obtain the VM ID (the vmid):

  ```
  # vim-cmd vmsvc/getallvms | grep -i vmname 5
  ```

5. Run the following commands to monitor the replication state, where the vmid is the value that is obtained in the previous step:

  ```
  # vim-cmd hbrsvc/vmreplica.getState vmid
  # vim-cmd hbrsvc/vmreplica.queryReplicationState vmid 6
  ```

6. ICMP Ping - Monitor the continuous ping started earlier.

An interruption might occur in the continuous ping during the switchover. However, the test ping quickly resumes after the **Migrate VM** task completes, as reflected in the Task console.

### Viewing migrated VMs

When Hybrid Cloud Services powers on a successfully migrated virtual machine, it powers off the original VM and stores it in a folder in vCenter. The stored virtual machines remain until it is manually deleted.

After the migration, view the vCenter and note the folders that are labeled **VMs migrated from the cloud** and **VMs migrated to the cloud**.
* As replicas, the powered-off VMs have the original name, with a binary time stamp appended.
* Migrated VMs can be treated like any other VMs. For example, they can be moved to a different location and powered on.
* Unwanted VMs within these folders can be deleted.
* Deletion is final, unless a backup solution is in place.

### Related links

* [Modifying or uninstalling HCX](/docs/services/vmwaresolutions/archiref/hcx-archi?topic=vmware-solutions-modifying-or-uninstalling-hcx)
