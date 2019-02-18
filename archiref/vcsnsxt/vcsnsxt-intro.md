---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---

# vCenter Server networking introduction

This document provides a view on the application modernization journey to {{site.data.keyword.cloud}}, focusing on the network aspects of the following platforms to allow an integrated multi-cloud to be used for application modernization:

- **VMware vCenter Server on IBM Cloud** - an offering from {{site.data.keyword.vmwaresolutions_short}}, which is a VMware-based platform that is automatically provisioned on {{site.data.keyword.cloud_notm}}.
- **IBM Cloud Private** - an application platform for developing and managing containerized applications, which are deployed on to a virtualized infrastructure platform, such as vCenter Server or an on-premises vSphere environment.
- **{{site.data.keyword.containerlong_notm}}** - a managed service on {{site.data.keyword.cloud_notm}} that uses Kubernetes as the orchestration engine for automating deployment, scaling, and operations of application containers across a single-tenant cluster.

The biggest challenges in application modernization are migration, networking, and security. vCenter Server, VMware Hybrid Cloud Extension (HCX), VMware NSX, {{site.data.keyword.containerlong_notm}}, and {{site.data.keyword.icpfull_notm}} help solve some of those challenges. The following network architecture describes an approach that uses Acme Skateboards as an example to connect components that are split across cloud and on-premises environments.

The [NSX-T preview](/docs/services/vmwaresolutions/archiref/vcsnsxt?topic=vmware-solutions-technology-preview-of-vmware-nsx-t-on-vmware-vcenter-server-on-ibm-cloud) is a technology preview to describe the use of VMware NSX Transformers (NSX-T) in a future reference architecture. NSX-T is designed to address application frameworks and architectures that have heterogeneous endpoints and technology stacks. In addition to vSphere, these environments can include other hypervisors, KVM, containers, and bare metal. NSX-T allows IT and development teams to choose the technologies best suited for their applications. NSX-T is also designed for management, operation, and consumption by development organizations in addition to networking teams.

## Application modernization on IBM Cloud

Application modernization is a term that describes the process of transitioning existing applications to use new development and delivery approaches on the cloud. Customers today are seeking innovative, efficient approaches that help them make this transition based on business and application complexity.

Business pressures demand faster time to market. Your existing estate includes not only applications, but data, processes, business logic, and user interfaces, all of which need to adapt to keep up with new business demands.

The benefits of application modernization include the following:

- Improves Developer productivity
- Increases operational efficiency
- Reduces cost to build new capabilities
- Expands capacity that is delivered in a short time

IBM understands that 70% of private cloud adoption is being driven by the need to modernize application environments, however, most organizations are approaching application modernization in a staged approach, which necessitates a hybrid and multi-cloud landscape, where:

- Complex and monolithic legacy applications that typically run on mainframes or UNIX systems remain on-premises.
- x86 environments used for Systems of Record (SoR), applications that are security sensitive, and regulated workloads are placed on a virtualized infrastructure or a private cloud.
- Applications such as SAP or high-performance computing consume bare metal resources.
- Security sensitive and some regulated workloads, which can move to the public cloud are moving to dedicated environments.
- Systems of Engagement (SoE) such as web, mobile, IoT, AI, or Video are moving to public clouds.

For example, a common pattern is to have front-end SoE applications that are deployed as containers with databases and legacy middleware that is deployed on VMs on a private cloud.

Because your IT infrastructure and business needs are unique, you need an approach to modernization that accelerates business value, minimizes delivery time, reduces your risks, and preserves your existing investments. IBM provides just such an approach to application modernization that is customizable to address your unique business and technology needs.

This document provides different views on the technologies that are used in the application modernization journey to {{site.data.keyword.cloud_notm}}:

* [vCenter Server and {{site.data.keyword.cloud_notm}} Private](/docs/services/vmwaresolutions/archiref/vcsicp?topic=vmware-solutions-vmware-vcenter-server-on-ibm-cloud-and-ibm-cloud-private-introduction) - A reference architecture for deploying the following platforms:
   - **VMware vCenter Server on IBM Cloud** - an offering from {{site.data.keyword.vmwaresolutions_short}} that is a VMware based platform that is automatically provisioned on {{site.data.keyword.cloud_notm}}.
   - **{{site.data.keyword.icpfull_notm}}** – {{site.data.keyword.icpfull_notm}} is an application platform for developing and managing containerized applications. It is an integrated environment that includes the container orchestrator Kubernetes, a private image repository, a management console, monitoring frameworks and a graphical user interface, which provides a centralized location from where you can deploy, manage, monitor, and scale your applications.
   - **IBM Cloud Automation Manager** – CAM is an enterprise-ready infrastructure as code platform that provides a single pane of glass to provision VM-based workloads alongside Kubernetes based workloads by using templates that are stored and versioned in a repository.
* [vCenter Server and {{site.data.keyword.containerlong_notm}}](/docs/services/vmwaresolutions/archiref/vcsiks?topic=vmware-solutions-vcenter-server-and-ibm-cloud-kubernetes-service-introduction) - A reference architecture for deploying the following platforms:
   - **VMware vCenter Server on IBM Cloud** - an offering from {{site.data.keyword.vmwaresolutions_short}} that is a VMware based platform that is automatically provisioned on {{site.data.keyword.cloud_notm}}.
   - **{{site.data.keyword.containerlong_notm}}** – a managed service on {{site.data.keyword.cloud_notm}} that uses Kubernetes as the orchestration engine for automating deployment, scaling, and operations of application containers across a single-tenant cluster.
* _vCenter Server networking_ - The current guide focuses on the network technologies that are used for integration between vCenter Server, {{site.data.keyword.icpfull_notm}}, and {{site.data.keyword.containerlong_notm}} such as NSX-V and Calico along with a technology preview of NSX-T.
* [VMware and Skate Advisor Concept Car](/docs/services/vmwaresolutions/archiref/vcscar?topic=vmware-solutions-vmware-and-skate-advisor-concept-car-introduction) - This reference architecture is a “concept car”, that is, a mechanism to highlight and show technologies solving real world problems. We wanted to demonstrate an interaction between Watson AI and machine learning in a real way. Through the culture of skateboarding, we demonstrate cloud services in a unique way. The implementation of the “concept car” is an extension to the Acme Skateboard application called Skate Advisor. Skate Advisor is a tool, which allows users to have skateboarding trick conversations with a Watson driven engine.
* [VMware: The modernization journey of Stock Trader](/docs/services/vmwaresolutions/archiref/vcscontent?topic=vmware-solutions-modernization-journey) - Our reference use case describes a classic WebSphere Application Server application being modernized using {{site.data.keyword.cloud_notm}} Private, IBM Middleware content, {{site.data.keyword.containerlong_notm}}, and vCenter Server on {{site.data.keyword.cloud_notm}}. We are all on a cloud journey, and we are all at different points on that journey. Through incremental steps by the application architect, Jane, and the cloud infrastructure architect, Todd, we modernize an existing application called Stock Trader. It shows examples that help you take each step in your journey, and the value that is realized to your business, regardless of how large or small each step is. We focus on four themes: applications, DevOps, integration, and management. All themes work together to help you achieve your goals. Modernizing one theme without the others might result in problems.

### Related links

* [vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle overview](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcenter-server-on-ibm-cloud-with-hybridity-bundle-overview)
