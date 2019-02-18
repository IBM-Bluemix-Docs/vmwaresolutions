---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---
# Installing and configuring hybrid services

The installer provisions and configures a virtual machine for each service virtual appliance. The service virtual machines are deployed both on-premises and in the cloud.

## Prerequisites

* The HCX Manager must be installed on premises, and registered with a VCF/VCS HCX enabled cloud endpoint.
* The target virtual data center must have sufficient resources.

## Configuration overview

The configuration procedure assumes that all service virtual appliances will be configured. However, they are not all required.
* The Hybrid Cloud Gateway is required.
* Installing WAN optimization is accomplished by checking the WAN Optimization Service box during the installation. No further configuration is required.
* To configure the Network Extension service, see the section _Configuring the Network Extension service_. The deployment of the optional appliance and can be deferred by returning to the Hybrid Services page and install the appliance later.

## Starting the Hybrid Service Virtual Appliance installation and configuration

The simple web interface is used to install the service virtual appliances and to configure more Layer 2 Concentrators.

### Prerequisite for installing and configuring the Hybrid Service Virtual Appliance

The HCX Manager must be installed and registered with the VCF/VCS HCX enabled cloud endpoint.

### Procedure to install and configure the Hybrid Service Virtual Appliance

1. Log in to the vSphere Web Client.
2. On the **Home** tab, click the **Hybrid Cloud Services** icon.
3. Click the **Hybrid Services** tab.
4. Click **Install Service**.
5. On the **Choose Hybrid Services** page, select the services to be installed, and click **Next**.

### What to do next

1. The next step is to configure the Hybrid Cloud Gateway if required.
2. A Layer 2 concentrator can be added to an existing installation at any time if sufficient resources are available to support the extension.

## Configuring the Hybrid Cloud Gateway

Configure the Hybrid Cloud Gateway service virtual appliance.

### Prerequisites for configuring the Hybrid Cloud Gateway

Follow the steps in _Starting the Hybrid Service Virtual Appliance installation and configuration_ and check Hybrid Cloud Gateway.

### Procedure to configure the Hybrid Cloud Gateway

On the **Hybrid Cloud Gateway** page, provide the following values and click **Next**:
* **Network** - The switch that connects the Hybrid Cloud Gateway management interface. In use cases 1 and 2, it can be a standard virtual switch or a virtual distributed switch. For any configuration that uses Layer 2 extension, it must be a virtual distributed switch.
* **Cluster/Host** - Select the Cluster or Host in which the Cloud Gateway is to be deployed.
* **Datastore** - Select the datastore where to deploy the Cloud Gateway.
* **VM/Hostname** - This value is optional.
* Provide the IP address/CIDR, Default Gateway, and DNS server to use for the Cloud Gateway management interface.
* To enter multiple addresses for the DNS server, separate them with commas.
* Under **Extended (optional)**, choose the vMotion network if applicable, and set the **admin** and **root** passwords. These passwords are specifically for the Hybrid Cloud Gateway appliance. The user name and password do not have to match the ones configured for the Hybrid Cloud Services appliance.

## Configuring the Network Extension service

Configure a Network Extension service either for single path deployment, or for a stand-alone network extension on an alternative path.

### Prerequisites for configuring the Network Extension service

Select the Network Extension service. If the Single Path configuration is installed, **Network Extension** is your only choice.

### Procedure to configure the Network Extension service

1. On the **Network Extension Service** page, select a virtual distributed switch from the **Distributed Switch** menu. When you install a standard Layer 2 Concentrator, the **Route stretched networks via Hybrid Cloud Gateway** check box will be available. It is not there for the high throughput L2C.
2. If **Route stretched networks via Hybrid Cloud Gateway** is selected, the installer determines a reasonable placement for the Layer 2 Concentrator (based on the switch) and populates the placement information. Otherwise, the placement information must be manually entered in the next step.
3. Set the route for the L2 Concentrator placement. If **Route stretched networks via Hybrid Cloud Gateway** was selected, these values cannot be edited.
  * **Network** - The deployment network for the Layer 2 Concentrator’s management interface.
  * **Compute** - The deployment cluster or host for the Layer 2 Concentrator.
  * **Datastore** - Deployment datastore for the Layer 2 Concentrator.
  * **VM/Hostname** - This value is optional.
4. Specify the Network Parameters for the local Layer 2 Concentrator.
  * If this option is disabled, use the default parameters that are provided by the installer.
  * If the port group selected in the **Network** menu from the Hybrid Cloud Gateway page is not part of the distributed switch, check **Specify the Network Parameters for the local Layer 2 Concentrator** and edit the **Extended Configurations** text boxes.
5. (Optional) **Extended Configurations** - Set the **admin** and **root** passwords for this specific Layer 2 Concentrator.
6. Click **Next**. On the **Ready to complete** page, review the information, and click **Finish**.

## Monitoring service appliance deployment

The task console can be used to monitor deployment progress for a service virtual machine.

### Procedure to monitor service appliance deployment

1. Log in to the vSphere Web Client. On the **Home** tab, click the **Hybrid Cloud Services** icon.
2. On the **Hybrid Cloud Services** pane, click the **Hybrid Services** tab. The virtual appliance deployment can be monitored from the Task console.
3. Go to the **Recent Tasks** pane and view the **All Users’ Tasks**.
4. Click **More Tasks** to open the Task console.
5. In the Task console, watch the deployment tasks.
6. When all tasks are completed, go to the inventory list and click **Hybrid Cloud Services**.
7. In the central pane, click the **Hybrid Services** tab.
8. Review the configuration summary for the hybrid service virtual appliances.

## Viewing tunnel status

View the Cloud Gateway tunnel status.

### Prerequisites for viewing tunnel status

The network extension service must be up if before you can stretch a network.

### Procedure to view tunnel status

1. To check the tunnel status from the Web client, select **Hybrid Cloud Services** in the inventory, and click the **Hybrid Services** tab.
2. To confirm a successful Hybrid Cloud Gateway tunnel, view the CGW (the acronym for the Hybrid Cloud Gateway) status as **Active**, and on the far right, the tunnel is color-coded green.

## Stretching a Layer 2 Network to IBM Cloud

Extend a Layer 2 network from the on-premises data center to VCF/VCS HCX enabled cloud.

### Prerequisites for stretching a Layer 2 Network to IBM Cloud

* Only VLAN tagged port groups (other than VLAN type None, or VLAN ID 0) can be stretched. VXLANs are considered VLANs.
* This procedure uses the **Extend Network** wizard. This wizard must be run from the vSphere® Web Client networking inventory view. Although the wizard is visible from other views, it must be run from the inventory context to get the correct information.

### Procedure to stretch a Layer 2 Network to IBM Cloud

1. Log in to the vSphere Web Client. On the **Home** tab in the central pane, click the **Networking** icon in the **Inventories** list.
2. In the **Networking** hierarchy, identify the port group for the network to be extended.
3. Right-click the port group, and from the menu, select **Hybridity Actions** and select **Extend Network**.
4. On the **Select source port groups** page, confirm the port group information and enter the **Gateway IP address** and prefix for the network. Click **Next**.
5. On the **Select destination gateway** page, complete the following steps:
  1. Select the VCF/VCS Hybrid Cloud Services Cloud Organization from the **Organization** menu.
  2. Select the VCF/VCS Hybrid Cloud Services Cloud virtual data center from the menu.
  3. Leave **Proximity Routing** disabled to force a VM within VCF/VCS Hybrid Cloud Services enabled cloud to always use the on-premises gateway to access the internet. By default, the traffic that originates from a VM in VCF/VCS Hybrid Cloud Services enabled cloud traverses the Layer 2 data path back to the on-premises data center and out to the default gateway. If **Proximity Routing** is checked, a VM within VCF/VCS Hybrid Cloud Services enabled cloud can access the internet without traversing the Layer 2 data path to vSphere.
  4. Select the remote destination gateway from the list of gateways by clicking the row. Click **Next**.
6. On the **Ready to complete** page, review all values provided. Click **Finish**.
7. To track the progress of the network extension, go to the **Recent Tasks** window, click the **All** tab, and view **All Users’ Tasks**.
8. To open the Task console, click **More Tasks**. The network extension is done when the **Extend Network** task status is **Completed**.

### Related links

* [Modifying or uninstalling HCX](/docs/services/vmwaresolutions/archiref/hcx-archi?topic=vmware-solutions-modifying-or-uninstalling-hcx)
