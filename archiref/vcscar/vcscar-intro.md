---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---

# VMware and Skate Advisor Concept Car introduction

The following reference architecture is a “concept car”, that is, a mechanism to
highlight and show technologies solving real world problems. The “concept car” in no way represents a
readily available service today.

The reference architecture also provides the following information:

-   Provides common language for the various stakeholders.
-   Provides consistency of technology implementation to solve problems.
-   Supports the validation of solutions against a proven reference
architecture.
-   Encourage adherence to common standards,
specifications, and patterns.

## About the ACME Skate Advisor

We wanted to demonstrate an interaction between Watson artificial
intelligence and machine learning in a real way and through it explore
deeper the culture of skateboarding. We demonstrate the available services and cloud infrastructure in a unique
way, demonstrating the technical capability and advancements in this
area. The implementation of the “concept car” is an extension to the
demonstrative Acme Skateboard application called Skate Advisor. Skate
Advisor is a tool, which allows users to have skateboarding trick
conversations with a Watson driven engine. The following quotations are a sample conversation:

-   “Watson, show me combinations of the trick Casper”
-   “Watson, show me common locations to perform a trick”
-   “Watson, show me a video of the trick Casper”

Acme Skate Advisor takes advantage of the Watson Discovery Service to
ingest articles, videos, blogs, and other Internet-based content to
create a learned database of tricks, which can be queried by the
application.

The Skate Advisor application is also implemented on the application
modernization platform, which provides container-based services through
{{site.data.keyword.icpfull_notm}} hosted on {{site.data.keyword.cloud_notm}} for VMware Services platform.

The Acme Skate Advisor application takes advantage of both the Watson
platform and the application modernization platform.

## Use cases

### Application modernization demonstration

Demonstrate an application that has been deployed to the application
modernization platform. The platform includes {{site.data.keyword.icpfull_notm}}, CAM, and NSX components
deployed on the {{site.data.keyword.cloud_notm}} for the VMware vCenter Server on {{site.data.keyword.cloud_notm}}
offering.

### Watson speech recognition With Watson Assistant

The Acme Skate Advisor communicates with users via a speech-to-text and
text-to-speech service that is provided with the Watson platform.

### Watson Discovery Service usage and training

The Acme Skate Advisor uses the Watson Discovery Services to keep
track of a database of Tricks for which a classification language is applied and the tricks discovered from online services.

### Watson services usage

The following Watson Services were used to create the Acme Skate
Advisor:
-   Watson Text to Speech.
-   Watson Speech to Text.
-   Watson Advisor.
-   Watson Discovery Service.
-   Watson Knowledge Studio.

## Application modernization on IBM Cloud

Application modernization is a term that describes the process of transitioning existing applications to use new development and delivery approaches on the cloud. Customers today are seeking innovative, efficient approaches that help them make this transition based on business and application complexity.

Business pressures demand faster time to market. Your existing estate includes not only applications, but data, processes, business logic, and user interfaces, all of which need to adapt to keep up with new business demands.

The following list describes the benefits of application modernization:
- Improves Developer productivity
- Increases operational efficiency
- Reduces cost to build new features
- Expands capacity that is delivered in a short time

IBM understands that 70 percent of private cloud adoption is driven by the need to modernize application environments. However, most organizations are approaching application modernization in a staged approach, which requires a hybrid and multi-cloud landscape, where:

- Complex and monolithic heritage applications that typically run on mainframes or UNIX systems stay on-premises.
- x86 environments used for Systems of Record (SoR), applications that are security sensitive, and regulated workloads are placed on a virtualized infrastructure or a private cloud.
- Applications such as SAP or high-performance computing use bare metal resources.
- Security sensitive and some regulated workloads, which can move to the public cloud are moving to dedicated environments.
- Systems of Engagement (SoE) such as web, mobile, IoT, AI, or Video are moving to public clouds.

For example, a common pattern is to have front end SoE applications that are deployed as containers with databases and heritage middleware that is deployed on VMs on a private cloud.

Because IT infrastructure and business needs are unique, an approach to modernization must provide the following priorities:

* Accelerate business value
* Minimizes delivery time
* Reduces risks
* Preserves existing investments.

IBM provides just such an approach to application
modernization that is customizable to address your unique business and
technology needs.

The following documents provide different views on the technologies that are used in the application modernization journey to {{site.data.keyword.cloud_notm}}:

* [vCenter Server and {{site.data.keyword.cloud_notm}} Private](/docs/services/vmwaresolutions/archiref/vcsicp?topic=vmware-solutions-vmware-vcenter-server-on-ibm-cloud-and-ibm-cloud-private-introduction) - A reference architecture for deploying the following platforms.
   - **VMware vCenter Server on IBM Cloud** - vCenter Server is an offering from {{site.data.keyword.vmwaresolutions_short}} that is a VMware based platform that is automatically provisioned on {{site.data.keyword.cloud_notm}}.
   - **{{site.data.keyword.icpfull_notm}}** – {{site.data.keyword.icpfull_notm}} is an application platform for developing and managing containerized applications. {{site.data.keyword.icpfull_notm}} is an integrated environment that includes the container orchestrator Kubernetes, a private image repository, a management console, monitoring frameworks, and a graphical user interface. The user interface provides a centralized location from where you can deploy, manage, monitor, and scale your applications.
   - **IBM Cloud Automation Manager** – CAM is an enterprise-ready infrastructure as code platform that provides a single pane of glass to provision VM-based workloads alongside Kubernetes based workloads by using templates that are stored and versioned in a repository.
* [vCenter Server and {{site.data.keyword.containerlong_notm}} service](/docs/services/vmwaresolutions/archiref/vcsiks?topic=vmware-solutions-vcenter-server-and-ibm-cloud-kubernetes-service-introduction) - A reference architecture for deploying the following platforms.
   - **VMware vCenter Server on IBM Cloud** - vCenter Server is an offering from {{site.data.keyword.vmwaresolutions_short}} that is a VMware based platform that is automatically provisioned on {{site.data.keyword.cloud_notm}}.
   - **{{site.data.keyword.containerlong_notm}}** – {{site.data.keyword.containerlong_notm}} is a managed service on {{site.data.keyword.cloud_notm}} that uses Kubernetes as the orchestration engine for automating deployment, scaling, and operations of application containers across a single-tenant cluster.
* [vCenter Server networking](/docs/services/vmwaresolutions/archiref/vcsnsxt?topic=vmware-solutions-vcenter-server-networking-introduction) - Focuses on the network technologies that are used for integration between vCenter Server, {{site.data.keyword.icpfull_notm}}, and {{site.data.keyword.containerlong_notm}} such as NSX-V and Calico along with a technology preview of NSX-T.
* _VMware and Skate Advisor Concept Car guide_ - A reference architecture that is a “concept car”, that is, a mechanism to highlight and show technologies solving real world problems. We wanted to demonstrate an interaction between Watson AI and machine learning in a real way. Through the culture of skateboarding, we demonstrate cloud services in a unique way. The implementation of the “concept car” is an extension to the Acme Skateboard application called Skate Advisor. Skate Advisor is a tool, which allows users to have skateboarding trick conversations with a Watson driven engine.
* [VMware: The modernization journey of Stock Trader](/docs/services/vmwaresolutions/archiref/vcscontent?topic=vmware-solutions-modernization-journey) - A reference use case that describes a classic WebSphere Application Server application that is modernized by using {{site.data.keyword.cloud_notm}} Private, IBM Middleware content, {{site.data.keyword.containerlong_notm}}, and vCenter Server on {{site.data.keyword.cloud_notm}}. We're all on a cloud journey, and we're all at different points on that journey. Through incremental steps by the application architect, Jane, and the cloud infrastructure architect, Todd, we modernize an existing application called Stock Trader. Review examples that help you take each step in your journey, and the value that is realized to your business, no matter how large, or small each step is. We focus on four themes: applications, DevOps, integration, and management. All themes work together to help you achieve your goals. Modernizing one theme without the others might result in problems.

### Related links

* [vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle overview](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcenter-server-on-ibm-cloud-with-hybridity-bundle-overview)
