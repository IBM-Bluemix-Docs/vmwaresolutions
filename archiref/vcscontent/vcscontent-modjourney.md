---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---

# Modernization journey

This is a reference use case on how a classic WebSphere Application Server application is modernized by using {{site.data.keyword.cloud}} Private, IBM Middleware content, {{site.data.keyword.containerlong_notm}}, and VMware vCenter Server on {{site.data.keyword.cloud_notm}}.

## Modernization is more than applications

We are all on a cloud journey, and we are all at different points on that journey. This use case focuses on how an existing application, Stock Trader, is modernized through incremental steps that the application architect, Jane, and the cloud infrastructure architect, Todd, planned out. This use case shows examples that help you take each step in your journey, and the value that is realized to your business, regardless of how large or small each step is.

Most of our focus in this journey is on modernizing the Stock Trader application. To fully modernize your business into a cloud-native business, the applications, DevOps, integration, and management themes must be discussed. All themes work together to help you achieve your goals. Modernizing one theme without the others might result in problems.

## Reasons to modernize

### Application modernization

The goal is cloud-native applications that scale and respond to quickly changing demands.

* You need to modernize existing apps and create new cloud-native apps to capture your customer's imagination.
* You need apps that can scale, reach worldwide, adjust to demands, change, enhance, and can pivot quickly.

### DevOps modernization

While you modernize your application, the way you deliver that application, the entire delivery pipeline, is modernized so the new cloud-native culture your Developers are creating can scale into how that app is delivered.

* You need to modernize your Development and Operations (and security) culture while you modernize your applications.
* You need DevOps teams that can scale, reach worldwide, adjust to demand, change, enhance, and can pivot quickly.

###  Integration modernization

All along the modernization journey, your teams need to integrate with existing assets, new cloud services, your data, and new insights from analytics performed on that data.

* You need to use your existing assets on this journey in a way that can scale, reach worldwide, adjust to demand, change, enhance, and can pivot quickly.
* You need to enrich with new cloud services at each step of this journey.
* You need to integrate your data and the insight you get from applying analytics to your data.

### Management

Modernizing your management practices is another parallel journey to take while you modernize your applications. The tools, culture, and core behaviors of how to manage and maintain a modernized application is far different than before.

* You need to manage your microservices, and containerized middleware by using built-in orchestration, logging, and monitoring.
* You need to manage your multi-cloud hybrid platforms across worldwide locations in a way that can scale, reach worldwide, adjust to demand, change, enhance, and can pivot quickly.
* You need to automate how you manage more than one cloud and the applications and middleware that run on them.

## Meet Todd and Jane

For our Stock Trader journey, we focus on two personas: Todd and Jane. Todd is operations lead for ACME company and is responsible for the infrastructure, security, cloud environments, and the policies that ensure the workloads that run in them comply with various regulations.

Jane is the development lead for the Stock Trader solution, and now has the responsibility to modernize Stock Trader, which means working across her development teams to change the development tools, culture and platforms, so the existing monolithic Stock Trader solution is modernized into a well run cloud native solution.

## Meet Stock Trader

Todd and Jane built an application that runs in WebSphere called Stock Trader. While it has a basic user interface, it is a dependable application where portfolio managers go to manage portfolios, including the buying and selling of stock, and viewing internal loyalty levels.

Stock Trader runs in WebSphere, is built with a few .war files, and uses a traditional Db2 database that runs in their data center that they depended on for years. It takes a long time to enhance this application because of dependencies between infrastructure teams, development teams, and data teams.

But, while Stock Trader is fine, everyone in the company wants something better. The product managers want to add social media to their loyalty program. Jane is happy because she can refactor the app into micro-services, which allows them to continuously deliver enhanced capabilities with fewer dependencies. Todd loves the idea of cloud efficiencies, but still requires governance to maintain compliance with corporate policies.

## Steps along the journey

Todd and Jane know from experience that a good journey to modernize solutions starts with a roadmap. While plans can change, it’s always good to think through the vision, and define a realistic path to get there. Each step must bring value to the company and the steps are not so significant that they cause costly interruptions to their clients.

For Todd and Jane, their steps in the Stock Trader journey are:
1. Lift Stock Trader VMs into {{site.data.keyword.cloud_notm}}. This step allows Todd to reduce the need for managing his own hardware and VMware content in the local data center.

2. Transform Stock Trader in WebSphere Application Server into Stock Trader in containers. This step increases resiliency because running containers in Kubernetes brings orchestration and other cloud behaviors. This does require Todd to prepare an {{site.data.keyword.cloud_notm}} Private instance in his VMware vCenter Server on {{site.data.keyword.cloud_notm}} environment, and then work with Jane and Transformation Advisor to containerize Stock Trader.

3. Refactor and add middleware into {{site.data.keyword.cloud_notm}} Private. This step brings their existing middleware into a cloud environment and optimizes cloud behaviors. This also streamlines licensing and prepares the solution to
be entirely portable for use in other Kubernetes environments.

4. Enrich with Watson and other public cloud services. This step can exponentially add value to the Stock Trader experience by pulling in AI services and the ability to communicate with worldwide cloud data centers.

5. True hybrid with {{site.data.keyword.cloud_notm}} Kubernetes Service. This step enables Todd to have a managed Kubernetes service that still connects to the same cloud region as his {{site.data.keyword.cloud_notm}} Private instance. It also enables Jane’s development teams to have a development and test cluster that they can experiment to while still accessing the same data source as their core {{site.data.keyword.cloud_notm}} Private cluster.

6. Modernize DevOps. Throughout this journey, Jane improves how she delivers Stock Trader.

7. Modernize Management. Todd and Jane worked to improve how they manage Stock Trader, and the platform it runs on, even across more than one cluster and cloud environment.

### Related links

* [vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle overview](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcenter-server-on-ibm-cloud-with-hybridity-bundle-overview)
