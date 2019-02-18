---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Staging and remediation

Patches and extensions can be optionally staged before remediation to ensure that they are downloaded from VUM to the vSphere ESXi host without applying the patches or extensions immediately. During remediation, VUM applies the patches, extensions, and upgrades to the inventory objects. Staging patches and extensions accelerates the remediation process because the patches and extensions are already available locally on the hosts.

If during the remediation process any host fails to enter maintenance mode, VUM reports an error and the remediation process stops and fails. The vSphere ESXi hosts that are already remediated remain at the updated level.

For the remediation process to work smoothly, it's advisable to disable some of the cluster features such as DPM, HA Admission Control, Fault Tolerance, and disconnecting any removable devices from the virtual machines (VMs) to avoid DRS issues while you migrate VMs to other hosts.
Also, while you run the remediation wizard, you can Generate Reports to verify that there are no inconsistent settings present at host/VM level that can cause the remediation process to fail.

1. Using the vSphere Web Client, select **Home** > **Hosts and Clusters**.
2. Right-click a datacenter, cluster, or a host, and click **Stage Patches**.
3. On the Baseline Selection page of the Stage wizard, select the patch and extension baselines to stage.
4. Select the hosts where patches and extensions are applied and click **Next**. If you selected to stage patches and extensions to a single host, it is selected by default.
5. Optionally, clear the patches and extensions to exclude from the stage operation. To search within the list of patches and extensions, enter text in the text box in the Filter box. Click **Next**.
6. Review the **Ready to Complete** page and click **Finish**.

The number of the staged patches and extensions for the specific host is displayed in the Patches and Extensions columns in the bottom pane of the Update Manager tab. After a remediation is successfully completed, all staged patches and extensions, whether installed or not during the remediation, will be deleted from the host.
Remediation is the process in which VUM applies patches, extensions, and upgrades to vSphere ESXi hosts, VMs, or virtual appliances after a scan is complete and makes the selected objects compliant. You can remediate single hosts, VMs, or virtual appliances or at a folder, cluster, or a data center level. VUM supports remediation for the following inventory objects by using either manual remediation or scheduled remediation:
* ESXi hosts for patch, extension, and upgrade remediation.
* Powered on, suspended, or powered off VMs and templates for VMware Tools and VM hardware upgrade.
* Powered on virtual appliances that are created with VMware Studio 2.0 and later, for virtual appliance upgrade.

If the update requires it, hosts are put into maintenance mode before remediation. The VCSA migrates the VMs to other hosts within VMware vCenter Server on {{site.data.keyword.cloud}} instance before the host is put in maintenance mode.

## For hosts in a vSAN cluster
Be aware of the following behavior for hosts that are part of a vSAN cluster:
* The host remediation process might take an extensive amount of time to complete.
* By design, only one host from a VSAN cluster can be in a maintenance mode at any time.
* VUM remediates hosts that are part of a VSAN cluster sequentially even if you set the option to remediate the hosts in parallel.
* Any VM on the host that uses a VM storage policy with a setting of 0 for **Number of failures to tolerate**, the host might experience unusual delays when it enters maintenance mode. The delay occurs because vSAN must migrate the VM data from one disk to another in the vSAN datastore cluster and this can take many hours. You can work around this by setting **Number of failures to tolerate** to 1 for the VM storage policy, which results in creating two copies of the VM files in the vSAN datastore.
* Any VM on the host that uses a VM storage policy with a setting of 1 for **Number of failures to tolerate**, then the VM becomes non-redundant when the host enters maintenance mode. If this is not acceptable, see [Virtual machine vSAN redundancy](/docs/services/vmwaresolutions/archiref/vum?topic=vmware-solutions-virtual-machine-vsan-redundancy).

To remediate hosts and clusters, follow these steps:
1. Use the vSphere Web Client, select **Home** > **Hosts and Clusters**.
2. From the inventory object navigator, select a data center, a cluster, or a host, click the **Update Manager** tab and click **Remediate**. If you selected a container object, all hosts under the selected object are remediated. The Remediate wizard opens.
3. Select **Patch Baselines** or **Extension Baselines** depending on what type of update you want to perform on the host. On the Select baseline page of the Remediate wizard, select the **baseline group** and **baselines** to apply.
4. Select the target hosts that you want to remediate and click **Next**. If you chose to remediate a single host and not a container object, the host is selected by default.
5. Optionally, on the **Patches and Extensions** page, clear specific patches or extensions to exclude them from the remediation process, and click **Next**.
6. Optionally, on the **Advanced options** page, select the option to schedule the remediation to run later and specify a unique name and an optional description for the task. The time that you set for the scheduled task is the time on the VCSA. Optionally, select the option to ignore warnings about unsupported devices on the host, or no longer supported VMFS datastore to continue with the remediation. Click **Next**.
7. On the Host **Remediation Options** page, from the **VM Power state** drop-down menu, you can select the change in the power state of the VMs and virtual appliances that are running on the hosts to be remediated. A host cannot enter maintenance mode until VMs on the host are powered off, suspended, or migrated with vMotion to other hosts in a DRS cluster. Some updates require that a host enters maintenance mode before remediation. VMs and appliances cannot run when a host is in maintenance mode. To reduce the host remediation downtime at the expense of VM availability, you can choose to shut down or suspend VMs and virtual appliances before remediation. In a DRS cluster, if you do not power off the VMs, the remediation takes longer but the VMs are available during the entire remediation process because they are migrated with vMotion to other hosts. The selections are as follows:

- **Power Off virtual machines** - Power off all VMs and virtual appliances before remediation.
- **Suspend virtual machines** - Suspend all running VMs and virtual appliances before remediation.
- **Do Not Change VM Power State** - Leave VMs and virtual appliances in their current power state.

8. Optionally, select **Disable any removable media devices connected to the virtual machine on the host**. VUM does not remediate hosts on which VMs have connected CD, DVD, or diskette drives. In cluster environments, connected media devices might prevent vMotion if the destination host does not have an identical device or mounted ISO image, which in turn prevents the source host from entering maintenance mode. After remediation, VUM reconnects the removable media devices if they are still available.
9. Optionally, select **Retry entering maintenance mode in case of failure**, specify the number of retries, and specify the time to wait between retries. VUM waits for the retry delay period and retries putting the host into maintenance mode as many times as you indicate in Number of retries field.

There is no requirement in a vCenter Server instance to select the check box under ESXi Patch Settings to enable Update Manager to patch powered on PXE booted ESXi hosts.
10. Click **Next**.
11. If you remediate hosts in a cluster, edit the cluster remediation options. The **Cluster remediation options** page is available only when you remediate clusters. The following options can be selected:
* **Disable Distributed Power Management (DPM)** if it is enabled for any of the selected clusters – VUM does not remediate clusters with active DPM. DPM monitors the resource use of the running VMs in the cluster. If sufficient excess capacity exists, DPM recommends moving VMs to other hosts in the cluster and placing the original host into standby mode to conserve power. Putting hosts into standby mode might interrupt remediation.
* **Disable High Availability admission control** if it is enabled for any of the selected clusters - VUM does not remediate clusters with active HA admission control. Admission control is a policy that is used by VMware HA to ensure failover capacity within a cluster. If HA admission control is enabled during remediation, the VMs within a cluster might not migrate with vMotion.
* **Disable Fault Tolerance (FT)** if it is enabled. This affects all fault tolerant VMs in the selected clusters. If FT is turned on for any of the VMs on a host, VUM does not remediate that host. For FT to be enabled, the hosts on which the Primary and Secondary VMs run must be of the same version and must have the same patches installed. If you apply different patches to these hosts, FT cannot be reenabled.
* **Enable parallel remediation for the hosts in the selected clusters** - Remediate hosts in clusters in a parallel manner. If the setting is not selected, VUM remediates the hosts in a cluster sequentially. You can select one of the following options for parallel remediation:
  - You can let VUM continuously evaluate the maximum number of hosts it can remediate concurrently without disrupting DRS settings.
  - You can specify a limit of the number of concurrently remediated hosts in each cluster you remediate. Note, VUM remediates concurrently only the hosts on which VMs are powered off or suspended. You can choose to power off or suspend VMs from the VM Power State menu in the Maintenance Mode Options pane on the Host Remediation Options page. By design only one host from a vSAN cluster can be in a maintenance mode at any time. VUM remediates hosts that are part of a vSAN cluster sequentially even if you select the option to remediate them in parallel.
* **Migrate powered off and suspended virtual machines to other hosts in the cluster**, if a host must enter maintenance mode. Update Manager migrates the suspended and powered off VMs from hosts that must enter maintenance mode to other hosts in the cluster. You can choose to power off or suspend VMs before remediation in the **Maintenance Mode Settings** pane.
12. On the Ready to complete page, you can optionally click **Pre-check Remediation** to generate a cluster remediation options report and click **OK**. A Cluster Remediation Options Report dialog box opens. You can export this report or copy the entries for your own record and click **Next**.
13. Review the **Ready to Complete** page and click **Finish**.

### Related links

* [VMware HCX on {{site.data.keyword.cloud_notm}} Solution Architecture](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf)
* [VMware Solutions on 	{{site.data.keyword.cloud_notm}} Digital Technical Engagement](https://ibm-dte.mybluemix.net/ibm-vmware) (demonstrations)
