---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---

# Network access and flows

## Container application access – IBM Cloud Private

There are three main ways to get external traffic and access into your Kubernetes cluster applications:

- NodePort
- LoadBalancer
- Ingress

### NodePort - IBM Cloud Private

Nodeports are a simple way of exposing external access to a workload for initial development and testing but not recommended for production. Ingress or load balancer is the recommended path.

### LoadBalancer - IBM Cloud Private

Currently, the {{site.data.keyword.icpfull_notm}} Platform supports an external Load Balancer for application workload.

### Ingress - IBM Cloud Private

An Ingress is a collection of rules that allow inbound connections to reach the cluster services. It can be configured to give services externally reachable URLs, load balance traffic, terminate SSL, offer name-based virtual hosting, and more.  The Proxy node in {{site.data.keyword.icpfull_notm}} infrastructure performs this function.

## Container application access – IBM Cloud Kubernetes Service

There are three main ways to get external traffic and access into your Kubernetes cluster applications:

- NodePort
- LoadBalancer
- Ingress

### NodePort - IBM Cloud Kubernetes Service

Nodeports are a simple way of exposing external access to a workload for initial development and testing but not recommended for production. Ingress or load balancer is the recommended path.

### LoadBalancer - IBM Cloud Kubernetes Service

Every {{site.data.keyword.containerlong_notm}} Cluster is provisioned with a public or private Application Load Balancer (ALB). The ALB uses a secured and unique public or private entry point to route incoming requests to your applications.

### Ingress - IBM Cloud Kubernetes Service

An Ingress is a collection of rules that allow inbound connections to reach the cluster services. It can be configured to give services externally reachable URLs, load balance traffic, terminate SSL, offer name-based virtual hosting, and more.

## Traffic flows

The following traffic flows are described:

- External user on the internet to a web tier hosted in a container in {{site.data.keyword.icpfull_notm}}.
- Web tier hosted in a container in {{site.data.keyword.icpfull_notm}} to database tier hosted in a virtual machine (VM) in VMware vCenter Server on {{site.data.keyword.cloud_notm}}.
- Enterprise user on the corporate network access to a VM in vCenter Server.

### External user on the internet to a web tier hosted in a container in IBM Cloud Private

1. The external user makes a request to the web tier by using the URL.
2.	DNS is used to determine the IP address. This IP address is an {{site.data.keyword.cloud_notm}} public address on a portable subnet that is assigned to the vCenter Server instance.
3.	The public network automatically forwards the request to the vSphere ESXi host  that hosts the ESG.
4.	The ESG forwards the request to the internal cluster IP address and port number of the ALB or Ingress Service. The IP packet is encapsulated in a VXLAN frame if the ESG and the ALB or Ingress Service are on different vSphere ESXi hosts. This internal cluster IP address is accessible inside the cluster only.
5.	Within the worker node, kube-proxy routes the request to the ALB or Ingress Service.
6.	If the application is on the same worker node, then iptables is used to determine which internal interface is used to forward the request. If the application is on a different worker node, then the Calico vRouter routes to the applicable worker node, by using IP-in-IP encapsulation. The IP-in-IP packet is encapsulated in a VXLAN frame for transport to the vSphere ESXi host where the worker node is located.

### Web tier hosted in a container in IBM Cloud Private to database tier hosted in a VM in vCenter Server

How the route tables in the ESG and vRouters are populated depends on the method of integration. See {{site.data.keyword.icpfull_notm}} and vCenter Server Integration.

1.	The web tier that runs in a container in {{site.data.keyword.icpfull_notm}} makes a request to a database that runs on a VM in the same vCenter Server instance.
2.	DNS is used to resolve the request to the IP address of the database.
3.	The container sends the request to the Calico vRouter.
4.	The vRouter has its route table that is populated with the IP address ranges hosted on the vCenter Server instance.
5.	The vRouter forwards the request but uses SNAT to change the source IP address from the IP address of the pod to the IP address of the worker node.
6.	The worker node that hosts the vRouter sends the request to the ESG.
7.	The ESG then forwards to the DLR.
8.	The DLR places the request onto the required VXLAN.
9.	The database VM receives the request.

### 	Enterprise user on the corporate network access to a VM in vCenter Server

1.	An enterprise user connected to the enterprise internal network makes a request of a resource on a VM hosted in vCenter Server.
2.	DNS is used to determine the IP address of the VM. This IP address is on a network that is stretched to {{site.data.keyword.cloud_notm}}.
3.	The on-premises router directs the traffic to the vSphere host that is hosting the L2 Concentrator.
4.	The L2 concentrator encapsulates the request in a secure tunnel and forwards it to the remote L2 Concentrator hosted in {{site.data.keyword.cloud_notm}} by using the private portable subnet IP address that is assigned to the device, via the on-premises router.
5.	The on-premises route looks in its routing table and discerns that the IP address for the remote L2 Concentrator needs to be sent to the WAN interface It forwards across the WAN, through the {{site.data.keyword.cloud_notm}} XCR router, via the BCR.
6.	The L2 Concentrator receives the request and places it on the VXLAN that hosts the stretched network.
7.	The VM receives the request.

## Public access network

{{site.data.keyword.icpfull_notm}} and CAM by default require internet connectivity to retrieve Docker images, Helm charts, Terraform templates, and operating system package managers.
In the latest releases, there is now support for proxy based installs for installations that are not directly connected to the internet and have options to install in an offline mode.

###	NSX firewall

The {{site.data.keyword.icpfull_notm}} NSX Edge firewall, is configured with rules to allow:
*	Enable VXLAN networks access to public access.
*	Enable VXLAN networks access to private {{site.data.keyword.cloud_notm}} network access.
*	Enable private {{site.data.keyword.cloud_notm}} network access to VXLAN networks.

### NSX NAT

The {{site.data.keyword.icpfull_notm}} NSX NAT, is configured with the following NATs:
*	SNAT for VXLAN networks access to public access.
*	SNAT for VXLAN networks access to private {{site.data.keyword.cloud_notm}} network access.
*	DNAT for {{site.data.keyword.icpfull_notm}} Cluster vIPs.

### Related links

* [vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle overview](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcenter-server-on-ibm-cloud-with-hybridity-bundle-overview)
