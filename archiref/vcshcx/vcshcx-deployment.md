---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-06"

---

# Cloud and client deployment

As described at the beginning of this document, a minimal HCX installation
consists of a single cloud and client-side deployment. The HCX client
side can install on any version of vSphere supported by HCX assuming that
there is network connectivity between the client and cloud sides.

## Requirements
- HCX Manager – CPU Count 4, Memory 12G, Disk 60G
- CGW – CPU Count 8, Memory 3G, Disk 2G
- L2C – CPU Count 8, Memory 3G, Disk 2G
- WAN Opt – CPU Count 8, Memory 14G, Disk 100G

##	Cloud

The cloud side HCX deployment is handled by the {{site.data.keyword.vmwaresolutions_full}} automation. The default configuration uses the public port
group for configuring any fleet components end-point connectivity. The
fleet components on the cloud side are deployed with their end point
interfaces configured with public IP addresses as they are security hardened
appliances. It is possible to deploy them behind a firewall. It is not
supported to have the client and cloud sides connect to
each other across an existing VPN tunnel. If you want to use
the private network for HCX endpoint connectivity, you can order HCX
cloud side for private network fleet deployment for use across dedicated
link such as MPLS.

## Client

The client-side HCX is user deployed and requires administrator
level permissions to the source vCenter. As of this writing, the HCX
client-side manager ova is approximately 1.7 GB. When use the {{site.data.keyword.vmwaresolutions_short}} console to order
HCX, a URL is provided with
a link to download the version of HCX for the client-side that matches
the version of HCX deployed on the cloud side. This link is provided in
the cloud side manager HCX user interface (UI).

A one-time use registration key is also provided. Use the following steps to configure the use registration.

1. Download HCX client (enterprise) OVA from the link provided in the
cloud side HCX UI.
    1. Log in to the cloud side HCX UI by using the HCX registration UI provided by IBM.
    2. Use the cloud vCenter ID and password to log in to the UI.
    3. On the **Administration** tab, select **request download link** to download the client-side OVA. Use a “jump box” that is local to the source vCenter where the OVA is deployed to complete this step.
2. Log in to vSphere C++ client (or web client with functioning client integration snap-in) and import the OVA that uses the vCenter import wizard.
    1. Ensure the network that the HCX manager is configured on has access to both the source vCenter and the internet.  
    2. Enter the registration key when prompted. (Use the web client if you have the client tools snap-in setup.)  
3. Log out and back into the vCenter web client. The **HCX** menu selection icon displays under the home screen menu.
4. For self-signed certificates, select the HCX menu item to access the HCX snap-in UI. Select the **Administration** tab.
    1. Select to import certificates from URL and key in the HCX cloud side registration URL provided by the {{site.data.keyword.vmwaresolutions_short}} console for HCX.
    2. Select **New Site Paring** in the **Site Parings** window pane within the **Dashboard** tab.
    3. Follow the prompts and provide the HCX cloud side registration URL and the Cloud side vCenter administrator ID and password.
    4. Continue to follow the prompts in the site registration wizard in configuring the Fleet components including the Cloud Gateway, Layer 2 Concentrator, and WAN Optimizer.  

For the client-side, use the **Tasks** menu to monitor the deployment of the Fleet components. For the cloud side deployment, use the **Tasks** menu in the vCenter web UI for the particular vCenter Server instance.

If there is a deployment failure on
either side, the fleet component deployments are backed out and
deleted. Upon determining the cause of the failure, click the **Interconnect** tab in the HCX vCenter web UI on the client-side, then
select **Install HCX Components** at the top of the screen.

Upon successful deployment of Fleet components and after several
minutes, the tunnel status for CGW and L2C components are in the **Up** status in the **Interconnect** tab.

## Related links

* [vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle
overview](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcenter-server-on-ibm-cloud-with-hybridity-bundle-overview)   
