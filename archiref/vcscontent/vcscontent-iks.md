---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---

# True hybrid with IBM Cloud Kubernetes Service

As Jane’s test team expands, she wanted to provide a test environment
that would run major portions of her application and still use the data she has
in her environment. Jane wants her test team to focus on testing
her application and not managing the Kubernetes cluster. Jane and Todd decide to stand up an [{{site.data.keyword.cloud}} Kubernetes
Service](https://www.ibm.com/cloud/container-service) instance and Jane
deploys Stock Trader, without code changes, into it.

Todd then adds the strongSwan VPN to connect between the private
networks of each cluster.

Figure 1. Stock Trader as a true hybrid application

![Stock Trader as a true hybrid application](vcscontent-truehybrid.svg)

## Related links

* [vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle overview](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcenter-server-on-ibm-cloud-with-hybridity-bundle-overview)
