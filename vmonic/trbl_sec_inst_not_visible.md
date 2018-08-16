---

copyright:

  years:  2016, 2018

lastupdated: "2018-08-16"

---

# Secondary vCenter Server system does not appear in the vSphere Web Client inventory

## Problem

In a multi-site configuration, after you add a new secondary instance, its vCenter Server system is not visible when logged in to the VMware vSphere Web Client of a previously ordered instance.

## Resolution

This is a known VMware 6.5 issue.

To resolve the problem, you must restart the vSphere Web Client:

1. Using the **root** account, connect over **ssh** to the vCenter VM (virtual machine) of the previously ordered instance.
2. Type ``shell`` to enter the bash shell.
3. Enter `service-control --stop vsphere-client` to stop the client.
4. Enter `service-control --start vsphere-client` to restart the client.
5. After the vSphere Web Client of the previously ordered instance is restarted, confirm that the vCenter Server system for the newly added secondary instance is visible in the vSphere Web Client.
