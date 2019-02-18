---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---

# IBM Cloud Private

{{site.data.keyword.icpfull_notm}} is an application platform for developing and managing containerized applications. It is an integrated environment that includes the container orchestrator Kubernetes, a private image repository, a management console, monitoring frameworks and a graphical user interface, which provides a centralized location from where you can deploy, manage, monitor, and scale your applications.

{{site.data.keyword.cloud_notm}} Private has the following features:
-	**Unified installer** – The installer rapidly sets up a Kubernetes based cluster with master, worker, and proxy nodes by using an Ansible based installer.
-	**{{site.data.keyword.cloud_notm}} Private management console** – Manage, monitor, and troubleshoot your applications and cluster from a single, centralized, and secure management console.
-	**Private Docker image registry** - This local registry has all the same features as Docker Hub but also allows you to restrict which users can view or pull images.
-	**Catalog of containerized software and services** - The catalog provides a centralized location from which you can browse for and install packages in your cluster. Packages for extra IBM products are available from curated repositories that are included in the default {{site.data.keyword.cloud_notm}} Private repository list.
-	**Isolated tenant networks** - Calico allows for improved performance and network isolation inside your cluster. With Calico, you can create an isolated subnet for each project inside your cluster. This network isolation provides you with added security during data transmissions and reduces the chances of compromising applications and their data. Calico also facilitates the creation of new network policies that can enable fine grained control over the sharing of objects within a single namespace.
-	**Robust monitoring and logging with ELK stack** - {{site.data.keyword.cloud_notm}} Private uses Elasticsearch, Logstash, Filebeat, and Heapster for the collection, storage, and querying of logs and metrics. This monitoring and logging process provides a centralized store for all logs and metrics, better performance, and increased stability when you access and query logs and metrics.

## IBM Cloud Private components

An {{site.data.keyword.cloud_notm}} Private cluster has four main classes of nodes: boot, master, worker, and proxy. You can optionally specify management, Vulnerability Advisor (VA), and etcd nodes in your cluster.
-	**Boot node** - A boot node is used for running installation, configuration, node scaling, and cluster updates.
-	**Master node** - A master node provides management services and controls the worker nodes in a cluster. Master nodes host processes that are responsible for resource allocation, state maintenance, scheduling, and monitoring.
-	**Worker node** - A worker node is a node that provides a containerized environment for running tasks. As demands increase, more worker nodes can easily be added to your cluster to improve performance and efficiency.
-	**Proxy node** - A proxy node is a node that transmits external request to the services created inside your cluster.
-	**Management node** - A management node is an optional node that hosts only management services such as monitoring, metering, and logging. By configuring dedicated management nodes, you can prevent the master node from becoming overloaded.
-	**Vulnerability Advisor (VA) node** - A VA node is an optional node that is used for running the Vulnerability Advisor services.
-	**etcd** node - An etcd node is an optional node that is used for running the etcd distributed key value store.

## IBM Cloud Private networking

{{site.data.keyword.icpfull_notm}} network management is facilitated by the use of Calico.
Calico uses layer 3 or the network layer, of the Open System Interconnection (OSI) model. Calico uses Border Gateway Protocol (BGP) to build routing tables that facilitate communication among agent nodes.

For more information about Calico networking, see [{{site.data.keyword.containerlong_notm}}](/docs/services/vmwaresolutions/archiref/vcsnsxt?topic=vmware-solutions-ibm-cloud-kubernetes-service).

### Related links

* [vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle overview](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcenter-server-on-ibm-cloud-with-hybridity-bundle-overview)
