---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---

# vCenter Server and IBM Cloud Kubernetes Service introduction

This document provides a view on the application modernization journey to {{site.data.keyword.cloud}}, focusing on the network aspects of the following platforms to allow an integrated multi-cloud to be used for application modernization:

This document provides a view of the application modernization journey to {{site.data.keyword.cloud_notm}}, focusing on the cloud management components to allow an integrated multi-cloud to be used for application modernization:

- **VMware vCenter Server on {{site.data.keyword.cloud_notm}}** - vCenter Server is an offering from {{site.data.keyword.vmwaresolutions_full}} and is a VMware based platform that is automatically provisioned on {{site.data.keyword.cloud_notm}}.
- **{{site.data.keyword.icpfull_notm}}** - {{site.data.keyword.icpfull_notm}} is an application platform for developing and managing containerized applications, which are deployed on to virtualized infrastructure platforms, such as VMware.
- **{{site.data.keyword.containerlong_notm}}** - {{site.data.keyword.containerlong_notm}} is a managed service on {{site.data.keyword.cloud_notm}} that uses Kubernetes as the orchestration engine for automating deployment, scaling, and operations of application containers across a single tenant cluster
- **IBM Multi-Cluster Manager** – MCM provides user visibility, application-centric management (policy, deployments, health, operations), and policy-based compliance across clouds and clusters. With MCM, you have control of your Kubernetes clusters.
- **{{site.data.keyword.cloud_notm}} Automation Manager** – CAM is a multi cloud, self-service management platform that runs on {{site.data.keyword.icpfull_notm}} that empowers Developers and administrators to meet business demands.

## Application modernization on IBM Cloud
Application modernization is a term that describes the process of transitioning existing applications to use new approaches on the cloud. Customers today are seeking innovative, efficient approaches that help them make this transition based on business and application complexity.

Business pressures demand faster time to market. Your existing estate includes not only applications, but data, processes, business logic, and user interfaces, all of which need to adapt to keep up with new business demands.

The benefits of application modernization include the following:
- Improved Developer productivity.
- Increased operational efficiency.
- Reduced cost to build new capabilities.
- Expanded capacity delivered in a short time.

IBM understands that 70% of private cloud adoption is driven by the need to modernize application environments, however, most organizations are approaching application modernization in a staged approach, which requires a hybrid and multi cloud landscape, where:
- Complex and monolithic legacy applications that typically run on mainframes or UNIX systems remain on-premises.
- x86 environments used for Systems of Record (SoR), applications that are security sensitive, and regulated workloads are placed on a virtualized infrastructure or a private cloud.
- Applications such as SAP or high-performance computing consume bare metal resources.
- Security sensitive and some regulated workloads, which can move to the public cloud are moving to dedicated environments.
- Systems of engagement (SoE) such as; web, mobile, IoT, AI, or Video are moving to public clouds.

For example, a common pattern is to have front end SOE applications that are deployed as containers with databases and legacy middleware that is deployed on VMs on a private cloud.

Because your IT infrastructure and business needs are unique, you need an approach to modernization that helps accelerate business value delivery, reduces your risks, and preserves your existing investments. IBM provides just such an approach that can be customized to address your unique business and technology needs related to application modernization.

This document is one of five documents that provides different views on the technologies that are used in the application modernization journey to {{site.data.keyword.cloud_notm}}:

* [vCenter Server and {{site.data.keyword.cloud_notm}} Private](/docs/services/vmwaresolutions/archiref/vcsicp?topic=vmware-solutions-vmware-vcenter-server-on-ibm-cloud-and-ibm-cloud-private-introduction) - A reference architecture for deploying the following platforms:
  - **VMware vCenter Server on {{site.data.keyword.cloud_notm}}** - an offering from {{site.data.keyword.vmwaresolutions_full}} and is a VMware based platform that is automatically provisioned on {{site.data.keyword.cloud_notm}}.
  - **{{site.data.keyword.cloud_notm}} Private** – an application platform for developing and managing containerized applications. {{site.data.keyword.icpfull_notm}} is an integrated environment that includes the container orchestrator Kubernetes, and a private image repository, a management console, monitoring frameworks and a graphical user interface, which provides a centralized location from where you can deploy, manage, monitor, and scale your applications.
  - **{{site.data.keyword.cloud_notm}} Automation Manager** – an enterprise-ready Infrastructure as Code (IaC) platform that provides a single pane of glass to provision VM-based workloads alongside Kubernetes based workloads by using templates that are stored and versioned in a repository.
* [vCenter Server and {{site.data.keyword.cloud_notm}} Private](/docs/services/vmwaresolutions/archiref/vcsiks?topic=vmware-solutions-vcenter-server-and-ibm-cloud-kubernetes-service-introduction) - A reference architecture for deploying the following platforms:
  - **VMware vCenter Server on {{site.data.keyword.cloud_notm}}** - an offering from {{site.data.keyword.vmwaresolutions_full}} and is a VMware based platform that is automatically provisioned on {{site.data.keyword.cloud_notm}}.
  - **{{site.data.keyword.containerlong_notm}}** – managed service on {{site.data.keyword.cloud_notm}} that uses Kubernetes as the orchestration engine for automating deployment, scaling, and operations of application containers across a single-tenant cluster.
* [vCenter Server networking](/docs/services/vmwaresolutions/archiref/vcsnsxt?topic=vmware-solutions-vcenter-server-networking-introduction) - Focuses on the network technologies that are used within vCenter Server, {{site.data.keyword.icpfull_notm}} and {{site.data.keyword.containerlong_notm}} such as NSX-V, NSX-T and Calico.
* [VMware and Skate Advisor Concept Car](/docs/services/vmwaresolutions/archiref/vcscar?topic=vmware-solutions-vmware-and-skate-advisor-concept-car-introduction) - This reference architecture is a “concept car”, that is, a mechanism to highlight and show technologies that solve real world problems. We wanted to demonstrate an interaction between Watson AI and machine learning in a real way. Through the culture of skateboarding, we demonstrate cloud services in a unique way. The implementation of the “concept car” is an extension to the Acme Skateboard application called Skate Advisor. Skate Advisor is a tool, which allows users to have skateboarding trick conversations with a Watson driven engine.
* [VMware: The modernization journey of Stock Trader](/docs/services/vmwaresolutions/archiref/vcscontent?topic=vmware-solutions-modernization-journey) - Our reference use case describes a classic WebSphere Application Server application being modernized using {{site.data.keyword.cloud_notm}} Private, IBM Middleware content, {{site.data.keyword.containerlong_notm}}, and vCenter Server on {{site.data.keyword.cloud_notm}}. We're all on a cloud journey and are at different points on that journey. Through incremental steps by the application architect, Jane, and the cloud infrastructure architect, Todd, we modernize an existing application called Stock Trader. It shows examples that help you take each step in your journey, and the value realized to your business, regardless of how large or small each step is. We focus on four themes: applications, DevOps, integration, and management. All themes work together to help you achieve your goals. Modernizing one theme without the others might result in problems.

### Related links

* [vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle overview](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcenter-server-on-ibm-cloud-with-hybridity-bundle-overview)
