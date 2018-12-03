---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-26"

---

# Creating baselines and attaching to inventory objects

Baselines have a collection of one or more patches, extensions, service packs, bug fixes, or upgrades, and can be classified as patch, extension, or upgrade baselines. Baseline groups are assembled from existing baselines. Host baseline groups can have a single upgrade baseline, and various patch and extension baselines. Virtual machine and virtual appliance baseline groups can have up to three upgrade baselines: one VMware Tools upgrade baseline, one virtual machine hardware upgrade baseline, and one virtual appliance upgrade baseline.

VUM includes predefined baselines, which you cannot edit or delete. You can use the predefined baselines, or create patch, extension, and upgrade baselines that meet your criteria. Custom baselines that you create, and the predefined baselines, can be combined in baseline groups.

VUM includes default baselines that you can use to scan any of the following devices to determine whether the hosts in your environment are updated with the latest patches, or whether the virtual appliances and virtual machines are upgraded to the latest version:
* Any virtual machine
* Any virtual appliance
* Any host

These pre-defined baselines are as follows:
* **Critical Host Patches (Predefined)** - Checks ESXi hosts for compliance with all critical patches.
* **Non-Critical Host Patches (Predefined)** - Checks ESXi hosts for compliance with all optional patches.
* **VMware Tools Upgrade to Match Host (Predefined)** - Checks virtual machines for compliance with the latest VMware Tools version on the host. Update Manager supports upgrading of VMware Tools for virtual machines on hosts that are running ESXi 5.5.x and later.
* **VM Hardware Upgrade to Match Host (Predefined)** - Checks the virtual hardware of a virtual machine for compliance with the latest version that is supported by the host. Update Manager supports upgrading to virtual hardware version vmx-13 on hosts that are running ESXi 6.5.
* **VA Upgrade to Latest (Predefined)** - Checks virtual appliance compliance with the latest released virtual appliance version.

To use baselines and baseline groups, you must attach them to selected inventory objects such as container objects, virtual machines, virtual appliances, or hosts. Although you can attach baselines and baseline groups to individual objects, a more efficient method is to attach them to container objects, such as folders, vApps, clusters or data centers. In this step, we use the predefined baselines against the hosts in the cluster.

1. Using the vSphere web Client, go to **Home** > **Hosts and Clusters**.
2. Click the cluster object that you want to scan.
3. Click **Attach Baseline**, and then select the two pre-defined Patch Baselines, then click **OK**.

### Related links

* [VMware HCX on {{site.data.keyword.cloud}} Solution Architecture](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf)
* [VMware Solutions on {{site.data.keyword.cloud_notm}} Digital Technical Engagement](https://ibm-dte.mybluemix.net/ibm-vmware) (demonstrations)
