---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-06"

---

# Troubleshooting

Review the following for common HCX issues and fixes.

## HCX Client user interface issues

### HCX user interface token time out

Typically, if the vCenter user interface (UI) has been left opened for some time, you may encounter a time-out in the HCX UI. This is because the login token to the HCX manager server has timed out. Log out of the vSphere web UI and back in to refresh the token.

### HCX Client UI displaying “NaN” for all metrics on the dashboard screen.

This issue is related to the permissions of the currently logged in vCenter account. Ensure that the Enterprise Administrator group is set in the HCX cloud side appliance manager UI.

## Migration issues

Migration issues in the current versions of HCX are usually in three categories: licensing, cloud gateway networking connectivity, and destination hardware compatibility.

### Licensing

If a migration fails because of a licensing issue, current versions of HCX clearly displays this in the error message with the client web UI within the vCenter UI.

### Network (WAN) connectivity

If there is an issue with WAN connectivity, always check the **Interconnect -> HCX Components** screen
within the HCX UI for tunnel status. The fleet components typically do not need to be reset or rebooted. If WAN connectivity is restored, they reconnect automatically.

If there are fixes and updates that were applied to the HCX Managers (Client and Cloud) and those updates also patch issues with the fleet components, you must redeploy the Cloud Gateway and any L2Cs deployed. It is possible to do further tunnel status debugging, by connecting to the HCX manager through a SSH client such as ccli  

1. SSH to the HCX manager using the admin account and the supplied password.
2. Run the `su –` command and the root password (same as admin password) to change to root.
3. Change the directory to `/opt/vmware/bin` and run the `./ccli` command. If this is not successful because the environment is not setup for root, run the `./ccliSetup.pl` command.
4. Run the `list` command within the ccli shell to list the fleet components registered with the HCX manager.
5. Select the focus of the ccli by typing the ID listed for the fleet component. For example, `go 8`.
6. Run the `debug remoteaccess enable` command to connect by using SSH to theconnect by using SSH desired fleet component.
7. Exit ccli and connect by using SSH to the IP address of the SSH enabled fleet component.
9. Continue to troubleshoot.
10. Return to the ccli and disable the ssh service for the component.
11. If necessary, use the `hc` ccli command to run a health check on the components.

## Destination hardware compatibility issues

vMotion migration can be an issue when the client source side is of newer hardware version and vSphere release than the cloud. Since replication based migration copies data to a newly built virtual machine (VM) on the destination side, changing the migration type to “Bulk Migration” should allow the migration to succeed in most cases.

## Stretched L2 issues

Few if any issues have been experienced with the operation of the L2 concentrator. Similar to the CGW, if the L2C loses connectivity it reconnects automatically after the network connectivity is restored. Use the ccli shell to check health and operation. After SSH is enabled and the L2C is connected, run the `ip tunnel` and `ip link |grep t_` commands to view the status of the tunnels.

## Related links

* [vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle
overview](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcenter-server-on-ibm-cloud-with-hybridity-bundle-overview)   
