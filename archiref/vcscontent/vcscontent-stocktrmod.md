---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Transform Stock Trader from WebSphere Application Server into Stock Trader in containers

The next step in the Stock Trader modernization journey is to transform the workload from running in virtual machines (VMs) to running in containers.

To continue, Todd and Jane run Transformation Advisor to analyze the Stock Trader workload, identify any migration complexity, and recommend changes. When ready, they use Transformation Advisor to deploy Stock Trader into Liberty containers that run in {{site.data.keyword.icpfull_notm}}.

## Prepare IBM Cloud Private

Todd first needs to install {{site.data.keyword.icpfull_notm}}. Since Todd has his VMware on {{site.data.keyword.cloud_notm}} environment, he decides to use the {{site.data.keyword.cloud_notm}} Private Hosted offering that gives him a complete {{site.data.keyword.icpfull_notm}} instance that runs on VMware VMs in {{site.data.keyword.cloud_notm}}.

The default dashboard provides a comprehensive user interface to manage the Kubernetes cluster, security, storage, and deploy from the catalog.

### Prepare storage

{{site.data.keyword.cloud_notm}} Private Hosted is configured out of the box with GlusterFS and provides file storage across VMs as dedicated GlusterFS nodes. The value of GlusterFS is that it enables dynamic provisioning. If Todd wants to, he can set up extra VMs as NFS servers.

Since Todd wanted an NFS server available to him, he identified a VM called ‘toddnfs’ and ran these
[steps](https://help.ubuntu.com/community/SettingUpNFSHowTo).

Todd runs the following commands to create a new NFS server:

`ssh root@toodnfs.acme.com`

`apt-get install nfs-kernel-server`

`mkdir -p /shared`

`chown nobody:nogroup /shared`

`vi /etc/exports`

Next, Todd adds the following line:

`/shared \*(rw,no_subtree_check,async,insecure,no_root_squash)`

`systemctl restart nfs-kernel-server`

Todd then runs the following command on each VM to install NFS onto each {{site.data.keyword.icpfull_notm}} worker VM:

`sudo apt-get update`

`sudo apt-get install nfs-common`

Todd runs the following command to confirm the installed version:

`apt-cache policy nfs-common`

Whenever a new NFS volume is needed, Todd runs the following command to create a new NFS volume, when necessary:

`cd /shared`

`mkdir -p <foldername>`

`chmod 777 <foldername>`

### Prepare image security

In {{site.data.keyword.icpfull_notm}} V3.1, security is enhanced by requiring an image policy in place before any image is pulled into an {{site.data.keyword.icpfull_notm}} instance. The enhancement requires that you add an image policy for where the IBM images reside, *dockerhub/ibmcom*, and in the docker store.

The ibmcloud-default-cluster-image-policy is provided by default and covers any IBM images in docker.io/ibmcom/\*, but since Db2 and other IBM content is located in the Docker Store another image policy for the docker store, *docker.io/store/ibmcorp/*, is necessary.

Additionally, some content requires a pod security policy set to allow specific access for the pod. For example, Db2 requires a policy for clients that want to run Db2 in a namespace other than 'default’.

Learn more in the [IBM Knowledge
Center](https://www.ibm.com/support/knowledgecenter/SSBS6K_3.1.0/manage_cluster/enable_pod_security.html).

## Deploy Transformation Advisor and Microclimate

After Todd has {{site.data.keyword.icpfull_notm}} running, he installs Transformation Advisor, along with Microclimate. Todd opens the [catalog](https://www.ibm.com/cloud/private/developer) and views all the available content.

Todd searches for Transformation Advisor and Microclimate and installs them using the provided readme file instructions when he clicks the helm chart.

### Run Transformation Advisor

To run Transformation Advisor, Jane added the data collector in the VM running Stock Trader in WebSphere opens the [Transformation
Advisor](https://developer.ibm.com/recipes/tutorials/using-the-transformation-advisor-on-ibm-cloud-private/) user interface to view the results.

Jane clicked Stock Trader and sees the recommendation to run each war file in Liberty, and that most of the migration would be simple with one moderate migration. Jane clicks Migration Details and sees the Transformation Advisor provides deployment files she can use to complete the migration. After Jane uploads the binary files into Transformation Advisor, it uses APIs provided by Microclimate to deploy the liberty containers.

In the end, the resulting Stock Trader layout options are:
* Single Liberty container - if Jane deploys a Liberty runtime and added her Stock Trader app into that single container.
* Multiple Liberty containers - one for each .war file as Transformation Advisor recommends for Stock Trader.

Todd didn't alter the data source during the transformation step. Transformation Advisor takes the WebSphere Application Server Network Deployment data source configuration and adds it to the Liberty container’s server.xml.
{:important}

### Related links

* [vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle overview](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcenter-server-on-ibm-cloud-with-hybridity-bundle-overview)
