## Notes for [Exam AZ-900: Microsoft Azure Fundamentals](https://docs.microsoft.com/en-us/learn/certifications/azure-fundamentals/)

## [syllabus](./syllabus/microsoft-certified-azure-fundamentals-skills-measured.pdf) as of 9/25/21

#### AWS to Azure services mapping
- [AWS to Azure services comparison](https://docs.microsoft.com/en-us/azure/architecture/aws-professional/services)

### Describe Cloud Concepts (20-25%)

#### Identify the benefits and considerations of using cloud services
- identify the benefits of cloud computing, such as High Availability, Scalability, Elasticity, Agility, and Disaster Recovery
- identify the differences between Capital Expenditure (CapEx) and Operational Expenditure (OpEx)
  - Capital Expenditure
    - Cost of acquiring infra
  - OpEx
    - Cost of continuing operation
- describe the consumption-based model

#### Describe the differences between categories of cloud services

- describe the shared responsibility model
- describe Infrastructure-as-a-Service (IaaS)
  - User manages OS and everything needed to run application
- describe Platform-as-a-Service (PaaS)
  - User manages data and software access
  - You manage the applications and services you develop, and the cloud service provider typically manages everything else.
  - https://azure.microsoft.com/en-us/overview/what-is-paas/
  - describe serverless computing
    - User only uses or pays for compute time when needed without deploying any compute resources
- describe Software-as-a-Service (SaaS)
  - User only uses the software without worrying about underlying details. e.g. gmail
- identify a service type based on a use case

#### Describe the differences between types of cloud computing

- define cloud computing
  - No servers on-premise
- describe Public cloud
  - In a public cloud, you share the same hardware, storage, and network devices with other organizations or cloud “tenants,” and you access services and manage your account using a web browser
- describe Private cloud
  - A private cloud consists of cloud computing resources used exclusively by one business or organization
- describe Hybrid cloud
  - combines on-premises infrastructure—or a private cloud—with a public cloud
- compare and contrast the three types of cloud computing

### Describe Core Azure Services (15-20%)

#### Describe the core Azure architectural components
- Overview: https://docs.microsoft.com/en-us/azure/azure-resource-manager/management/overview#understand-scope
- describe the benefits and usage of Regions and Region Pairs
  - Geography contains one or more regions 
    - Geographies are fault-tolerant to withstand complete region failure
    - Geographies allow customers with specific data-residency and compliance needs to keep their data and applications close
  - Region pair consists of two regions within same geography
    - Azure planned maintenance affects one region at a time
    - https://docs.microsoft.com/en-us/azure/best-practices-availability-paired-regions
- "Fault Domain" is a collection of servers that share common resources such as power and network connectivity.
- "Availability Set" refers to two or more Virtual Machines deployed across different Fault Domains to avoid a single point of failure.
- describe the benefits and usage of Availability Zones
  - Multi AZ deployment protects from Data center failure 
  - AZs are distinct physical locations within region
    - Each AZ may have one or more data centers equipped with independent power, cooling and networking
- describe the benefits and usage of Resource Groups
  - A container to group/hold related resources for a solution or resources that make sense to grouped together
  - Logical containers that you use to group related resources in a subscription
  - RG can contain resources that share same lifecycle, you can easily update,delete, deploy them as a group
  - https://docs.microsoft.com/en-us/azure/azure-resource-manager/management/manage-resource-groups-portal
  - RG stores metadata about resources in the region you selected
  - You can apply tags to RG
    - Tags applied to the resource group or subscription aren't inherited by the resources
- describe the benefits and usage of Subscriptions
  - Creating a subscription is the first step in adopting Azure
  - Decides who pays, boundary of scale
  - Establish a structure to organize and manage assets
  - Every Azure resource is logically associated with only one subscription. You can move a resource to another subscription later.
- describe the benefits and usage of Management Groups
  - https://docs.microsoft.com/en-us/azure/governance/management-groups/overview
  - Logical containers that you use for one or more subscriptions
  - For example:
    - you can apply policies to a management group that limits the regions available for virtual machine (VM) creation. 
      - This policy would be applied to all management groups, subscriptions, and resources under that management group by only allowing VMs to be created in that region.
- describe the benefits and usage of Azure Resource Manager
  - https://docs.microsoft.com/en-us/azure/azure-resource-manager/management/overview
- explain Azure resources
  - Resource: An entity that's managed by Azure

#### Describe core resources available in Azure

- describe the benefits and usage of Virtual Machines, Azure App Services, Azure Container Instances (ACI), Azure Kubernetes Service (AKS), and Windows Virtual Desktop
- describe the benefits and usage of Virtual Networks, VPN Gateway, Virtual Network peering, and ExpressRoute
- express route: dedicated connection
- Azure Virtual Network
  - The Azure Virtual Network service is used to define an isolated network in Azure. The virtual network can then be used to host your resources such as Azure virtual machines.
  - The Azure virtual network gets assigned an address space which you specify when you create an Azure virtual network
  - You can then add subnets to your Azure virtual network. This helps divide your network into more logical segments.
  - An example is shown below of having multiple subnets. You could have one subnet named SubnetA in the virtual network to host your Web servers and another subnet to host the Database servers.
  - When you create a virtual machine in a virtual network, the virtual machine gets a Private IP address from the address space of the subnet is it launched in.
- Network Security Groups
  - These are used to filter network traffic to and from Azure resources in an Azure virtual network.
  - A network security group is attached to the network interface attached to the virtual machine.
  - A network security group consists of Inbound rules that are used to control the traffic inbound into a virtual machine
  - By default all traffic into a virtual machine is DENIED.
  - You have explicitly add rules to allow traffic into a virtual machine
  - There are also outbound rules to control the traffic flowing out of the virtual machine. By default all traffic outbound onto the Internet is allowed.
- Virtual Network Peering
  - Virtual Network Peering is used to connect two Azure virtual networks together via the backbone network.
  - Azure supports connecting two virtual networks located in the same region or networks located across regions.
  - Once you enable virtual network peering between two virtual networks, the virtual machines can then communicate via their private IP addresses across the peering connection.
  - You can also peer virtual networks that are located across different subscriptions.
  - The virtual networks can't have overlapping CIDR blocks.
- Point-to-Site VPN Connection
  - A Point-to-Site VPN connection is used to establish a secure connection between multiple client machines and an Azure virtual network via the Internet.
  - Below is a diagram from the Microsoft documentation on a sample scenario
  - Image reference -https://docs.microsoft.com/en-us/azure/vpn-gateway/vpn-gateway-howto-point-to-site-resource-manager-portal
  - To implement a Point to Site VPN connection, you need to create a VPN Gateway in Azure.
- Site-to-Site VPN Connection
  - A Site-to-Site VPN connection is used to establish a secure connection between an on-premise network and an Azure network via the Internet.
  - Below is a diagram from the Microsoft documentation on a sample scenario
    - Image reference - https://docs.microsoft.com/en-us/azure/vpn-gateway/vpn-gateway-howto-site-to-site-resource-manager-portal
  - On the on-premise side, you need to have a VPN device that can route traffic via the Internet onto the VPN gateway in Azure. The VPN device can be a hardware device like a Cisco router or a software device ( e.g Windows Server 2016 running Routing and Remote services). The VPN device needs to have a publicly routable IP address.
  - The subnets in your on-premise network must not overlap with the subnets in your Azure virtual network
  - The Site-to-Site VPN connection uses an IPSec tunnel to encrypt the traffic.
  - The VPN gateway resource you create in Azure is used to route encrypted traffic between your on-premise data center and your Azure virtual network.
- describe the benefits and usage of Container (Blob) Storage, Disk Storage, File Storage, and storage tiers
- Azure Storage Accounts
  - Types of storage accounts
    - General-purpose v2 accounts – This is recommended for most scenarios. This storage account type provides the blob, file , queue and table service.
    - Premium block blobs – This is specifically when you want premium performance for storing block or append blobs.
    - Premium file shares – This is specifically when you want premium performance for file-only storage.
    - Premium page blobs – This is specifically when you want premium performance for page blobs.
- The most common type of storage account is the General Purpose v2 storage account.
- Use case scenarios for the different services in a General Purpose v2 storage account
- Blob service
  - This is object storage for the cloud.
  - Here you can store massive amounts of unstructured data on the cloud.
  - This is highly recommended when you want to store images, documents, video and audio files.
  - Within the blob service, you create a container that is used to store the blob objects.
  - There are three different types of blobs
  - Block blobs – This is used for storing text and binary data.
  - Append blobs – This is ideal for logging data.
  - Page blobs – This is used to store virtual hard disk files for Azure virtual machines.
  - To use the Blob service you have to first create a container and then upload the blobs or objects into the container.
  - When you upload an object or blob to the service, each bob gets a unique URL which you can access if you are assigned the right permissions
- File service 
  - Use this service if you need to store files that need to be accessed by machines using the SMB (Server Message Block) protocol
  - In the File service, you can first go ahead and create a file share.
  - You can then mount this file share from different machines. You can't mount drives with the Blob service.
- Table service 
  - Use this if you want to store NoSQL data or table like data.
  - It's easy and simple to create a table and add data from the Azure portal itself.
- Queue service 
  - Use this if you want to exchange messages between components of your application
- Azure Storage Accounts 
- Replication
  - There are different replication techniques available to make your data highly available.
  - The different replication techniques available
  - Locally-redundant storage (LRS) - Here data is replicated synchronously three times within a physical location in the primary region.
  - Zone-redundant storage (ZRS) - Here data is replicated synchronously across three Azure availability zones in the primary region. This is good when you want to have data present even in the event of a data center failure.
  - Geo-redundant storage (GRS) - Here data is replicated synchronously three times in the primary region, then replicated asynchronously to the secondary region.
  - Read access Geo-redundant storage (RA-GRS) - Here data is replicated synchronously three times in the primary region, then replicated asynchronously to the secondary region. 
    - Here the data in the secondary region is also available for read-only purposes.
- Azure Storage Accounts - Access tiers
  - Access tiers help you optimize the storage costs and access costs for your data. 
  - The different access tiers are
  1. Hot – This is optimized for storing data that is accessed frequently. This can be set at the account level.
  2. Cool – This is optimized for storing data that is infrequently accessed and stored for at least 30 days. This can be set at the account level.
     - Note:- For the Cool Access tier, the storage costs are lower than the Hot tier. But the access costs are higher than the Hot access tier.
  3. Archive tier - This is optimized for storing data that is rarely accessed and stored for at least 180 days. This can be set only at the blob level.
   - Note:- When a blob is in the archive tier, you can’t access the blob. You have to rehydrate the blob first before it can be accessed.
   - Also, the storage costs are the least when it comes to the Archive access tier. But the access costs are the highest.
- describe the benefits and usage of Cosmos DB, Azure SQL Database, Azure Database for MySQL, Azure Database for PostgreSQL, and SQL Managed Instance
- Azure SQL Database (Platform as a service)
  - This is a service that allows you to create a managed Microsoft SQL Server database on the cloud. The advantages of using this service
  - You don't have to manage the underlying infrastructure. This is managed by Azure.
  - You have a variety of purchasing options
  - You have automated backups. This reduces the burden of managing backups.
  - It gives you a service level agreement of 99.99%
  - If you need to have more control over the database engine, then consider installing the SQL Server engine on an Azure virtual machine.
- Azure Synapse Analytics
  - This was formerly known as Azure SQL Data warehouse.
  - This service is used for enterprise data warehousing and Big Data Analytics
  - When you want to perform analysis on a large data set , consider using this service.
- Azure Cosmos DB
  - This is a data store that companies can opt for, when they want to get low latency access to their data, and they want high availability for their data.
  - It is a multi-model database. This means you can choose from a variety of options when it comes to what type of data you want to store in the account.
- describe the benefits and usage of Azure Marketplace

### Describe core solutions and management tools on Azure (10-15%)

#### Describe core solutions available in Azure

- describe the benefits and usage of Internet of Things (IoT) Hub, IoT Central, and Azure Sphere
- describe the benefits and usage of Azure Synapse Analytics, HDInsight, and Azure Databricks
- describe the benefits and usage of Azure Machine Learning, Cognitive Services and Azure Bot Service
- Application Insights
  - Equivalent to NewRelic 
  - Application Performance Management service for web developers.
  - You can use this tool to monitor your applications.
  - It can help developers detect anomalies in the application.
  - It can help diagnose issues.
  - It can also help understand how users use your application.
  - It also helps you improve performance and usability of your application.
  - How does it work
    - You install a small instrumentation package within your application.
    - You can see the statistics of your application locally in Visual Studio as you run your application.
    - You can also use the Application Insights resource in Azure to monitor your application.
    - What are the different aspects monitored by Application Insights
    - Request rates, the response times and failure rates – This is done at the page level.
    - Exception recorded by your application.
    - Page views and their load performance as reported from the user’s browser.
    - User and session counts.
    - Performance counters of the underlying Windows or Linux Machines.
    - Diagnostic trace logs from your application.
    - Any custom events or metrics that the developer writes themselves in the code.
- Azure Cognitive services
  - Azure Cognitive Services are API’s , SDK’s and services available for helping developers building intelligent applications.
  - Computer Vision – This helps developers process images and return information. You just supply the image, and the service can help identify the image.
    - This service can detect objects, help provide categories for the image.
    - It can also detect color , faces , help describe an image.
    - It can also extract text from images.
    - It can also help moderate content in images.
  - Face API – This can be used to detect, recognize and analyze human faces in images.
    - It can also help find similar faces from a set of images.
    - It can also help identify a detected face against a database of people.
  - Speech services
    - You can use the Speech-to-Text service to translate speech to text.
    - You can also generate synthesized speech from text using Text-to-Speech.
- Azure Machine Learning
  - Machine learning is the process that enables computers to use existing data to forecast future behaviors , outcomes and trends.
  - Here the computers don’t need to be programmed on how to learn.
  - Azure Machine Learning gives you a cloud-based environment for preparing data, train the data, testing, deploying and managing machine learning models.
  - You get a visual interface which can be used to drag and drop modules to build experiments and deploy models.
  - Machine Learning Studio – This is a drag-and-drop visual workspace which you can use to build, test and deploy machine learning solutions without the need of writing any sort of code.
  - This tool has prebuilt and preconfigured machine learning algorithms.
- Azure HDInsight
  - This is a cloud distribution of Hadoop based components.
  - Azure HDInsight allows you to process large amounts of data.
  - You can use HDInsight for a variety of big data processing scenarios such as Data warehousing , Batch processing and for Data science as well.
  - You can create different types of clusters – Apache Hadoop, Apache Spark, Apache Hbase.
  - HDInsight also supports a host of programming languages such as Java, Python,.Net and Go.
- Azure DevOps
  - This is a complete set of tools that can be used to help teams to plan work, collaborate on code development and build and deploy applications.
  - Azure DevOps have the following services in place
  - Azure Repos – This allows you to host Git repositories or use Team Foundation Version Control.
  - Azure Pipelines – This provides build and release services for continuous integration and release.
  - Azure Boards – This helps to plan and track work items.
  - Azure Test Plans – This provides tools for testing of applications.
  - Azure Artifacts – This allows teams to share Maven, npm and NuGet packages from public and private sources.
- Azure DevTest Labs
  - This service allows developers to efficiently self-manage virtual machines and PaaS resources without the need to wait for approvals.
  - The DevTest Labs can be used to create labs consisting of pre-configured bases or Azure Resource Manager templates.
  - With DevTest Labs, you can quickly provision Windows and Linux based environment through the use of reusable templates and artifacts.
  - You can easily create load testing environments and create environments for training and demos.
  - This service also helps in optimizing costs through the following features
  - Here you can set an auto-shutdown and auto-start schedules for virtual machines.
  - You can set policies on the number of virtual machines users can create.
  - You can set policies on the size of the virtual machine.
  - You can track costs.

- describe the benefits and usage of serverless computing solutions that include Azure Functions and Logic Apps
- Azure App Service
  - This is an HTTP-based service that allows you to host web applications, REST API's and mobile back ends. You can develop a program in programming languages such as .NET, .NET Core, Java, Ruby, Node.js, PHP and Python.
  - Here you don't need to manage the underlying infrastructure. It allows you to focus on code development.
  - Each App service needs to be associated with an App Service Plan.
  - Each App service plan has an associated cost per month and also has specific features based on the plan you choose.
- Virtual Machine Scale Sets
  - This service allows you to create and manage a group of identical load balanced virtual machines.
  - Here the number of Virtual Machine instances in the scale set can scale based on demand
  - This is the best service if you want to add scalability to your application
- Azure Load Balancer
  - The Azure Load balancer is used to distribute incoming network traffic to a backend group of servers.
  - This service helps increase the availability of your entire application architecture
  - Here the Load Balancer would take the incoming requests from the users and direct the requests to virtual machines running in an Azure virtual network.
  - If you have a web application running on the backend virtual machines, the requests would be distributed across the virtual machines by the Azure Load Balancer.
- Other tools to access Azure resources
- You can use other tools to access and work with Azure resources
  - You can use PowerShell which can work on Windows, macOS and Linux
  - You can use the Azure command line interface which can work on Windows, macOS and Linux
  - You can use Azure cloud shell from the browser, which can then work on any operating system which has browser support
- Azure Functions
  - This service allows you to run small pieces of code as functions.
  - Here you just develop and upload the code to an Azure Function.
  - You only get billed for the amount of time the code is run.
  - You can use a variety of programming languages in Azure Functions.
  - C#, Java , JavaScript, PowerShell and Python.
  - You can use libraries by using NuGet and NPM packages.
    - Pricing plans available for Azure Functions
    - Consumption Plan – Here you only pay for the time the code runs.
    - App Service Plan – If you already have an App Service plan that runs a web application, you can reuse the same plan to run Azure Functions. This would save on cost if you already have an App Service Plan in place.
    - Premium Plan – Here you get a number of **pre-warmed instances** that are always online and ready to run your functions. The plan also automatically adds more compute when required.
  - You can also invoke your functions via various triggers
- Azure Logic Apps
  - This is a cloud service that helps you schedule, automate and orchestrate tasks , business processes and workflows.
  - How it works
  - You first design a workflow in Azure Logic Apps
  - Each workflow starts with a trigger.
  - The trigger is fired via a specific event
  - When the trigger is fired , the Logic App engine creates a logic app instance that runs the workflow.
  - Connectors for Azure Logic Apps
  - These connectors provide easy access to event, data and actions that are sent from external applications, services , systems or platforms.
  - You have built-in connectors that can connect to Azure services such as Azure functions, Azure API Apps etc.
  - You have Managed connectors that can connect to platforms such as Office 365, Microsoft Dynamics.
- Azure Traffic Manager
  - The Azure Traffic Manager service is a DNS-based traffic load balancer that distributes traffic across services that are distributed across different Azure regions.
  - The Traffic Manager service is used to direct client requests to the most appropriate service endpoint that is based on a traffic-routing method and the health of the endpoints.
  - The different traffic routing methods available for the Azure Traffic Manager are
    - Priority – Route traffic to another endpoint in case the primary fails.
    - Weighted – Route traffic to different endpoints based on weight.
    - Performance - you want end users to use the "closest" endpoint in terms of the lowest network latency.
    - Geographic - geographic location their DNS query originates from.
    - Multivalued – Here different endpoints are sent to the client. The client then selects the endpoint to send the request to.
    - Subnet – This maps a set of end-user IP address ranges to a specific endpoint within a Traffic Manager profile.
- describe the benefits and usage of Azure DevOps, GitHub, GitHub Actions, and Azure DevTest Labs

#### Describe Azure management tools

- describe the functionality and usage of the Azure Portal, Azure PowerShell, Azure CLI, Cloud Shell, and Azure Mobile App
- describe the functionality and usage of Azure Advisor
  - Azure Advisor—your free, personalized guide to Azure best practices
- describe the functionality and usage of Azure Resource Manager (ARM) templates
  - Infra as code
- describe the functionality and usage of Azure Monitor
- describe the functionality and usage of Azure Service Health
  - Personalized alerts and guidance for Azure service issues

### Describe general security and network security features (10-15%)

#### Describe Azure security features

- describe basic features of Azure Security Center, including policy compliance, security alerts, secure score, and resource hygiene
- describe the functionality and usage of Key Vault
- describe the functionality and usage of Azure Sentinel
- describe the functionality and usage of Azure Dedicated Hosts

#### Describe Azure network security

- describe the concept of defense in depth
- describe the functionality and usage of Network Security Groups (NSG)
  - Use an Azure network security group to filter network traffic to and from Azure resources in an Azure virtual network
- describe the functionality and usage of Azure Firewall
- describe the functionality and usage of Azure DDoS protection

### Describe identity, governance, privacy, and compliance features (20- 25%)

#### Describe core Azure identity services

- explain the difference between authentication and authorization
- define Azure Active Directory
- describe the functionality and usage of Azure Active Directory
- describe the functionality and usage of Conditional Access, Multi-Factor Authentication (MFA), and Single Sign-On (SSO)

#### Describe Azure governance features

- describe the functionality and usage of Role-Based Access Control (RBAC)
  - If control of an action is required, then Azure RBAC is the correct tool to use
  - https://docs.microsoft.com/en-us/azure/role-based-access-control/overview#scope
- describe the functionality and usage of resource locks
  - As an administrator, you can lock a subscription, resource group, or resource to prevent other users in your organization from accidentally deleting or modifying critical resources.
  - CanNotDelete means authorized users can still read and modify a resource, but they can't delete the resource. 
  - ReadOnly means authorized users can read a resource, but they can't delete or update the resource. Applying this lock is similar to restricting all authorized users to the permissions granted by the Reader role.
  - The lock overrides any permissions the user might have.
  - It's important to understand that locks don't apply to all types of operations. 
  - Azure operations can be divided into two categories - control plane and data plane. 
  - Locks only apply to control plane operations
    - Control plane operations are operations sent to https://management.azure.com
  - Lock inheritance 
    - When you apply a lock at a parent scope, all resources within that scope inherit the same lock. 
    - Even resources you add later inherit the lock from the parent. 
    - The most restrictive lock in the inheritance takes precedence
- describe the functionality and usage of tags
  - maximum of 50 tag name/value pairs are allowed
- describe the functionality and usage of Azure Policy
  - Azure Policy evaluates resources in Azure by comparing the properties of those resources to business rules
- The combination of Azure RBAC and Azure Policy provides full scope control in Azure.
- describe the functionality and usage of Azure Blueprints
  - A blueprint is a package or container for composing focus-specific sets of standards, patterns, and requirements related to the implementation of Azure cloud services, security, and design that can be reused to maintain consistency and compliance.
    - Blueprints are a declarative way to orchestrate the deployment of various resource templates and other artifacts such as:
      - Role Assignments
      - Policy Assignments
      - Azure Resource Manager templates (ARM templates)
      - Resource Groups
  - This is a service that allows you to define a repeatable set of Azure resources. 
  - The definition of the Azure resources can adhere to an organization’s standards, patterns and requirements. 
  - Using blueprints , you can orchestrate the deployment of resources such as role assignments, policy assignments, Azure resource manager templates and resource groups. 
  - Some differences between Azure blueprints and resource manager templates 
    - You can use blueprints to upgrade several subscriptions at once . 
    - The relationship between the blueprint definition and the blueprint assignment is reserved.
- Azure Security Center 
  - This is an infrastructure security management system. 
  - You can use this tool to improve the security of your Azure based resources and on-premise resources as well. 
  - Azure Security Center has in-built support for services such as Azure virtual machines , Function Apps, Azure SQL Server databases. 
  - You can also allow Azure Security Center to give recommendations on what to do for on-premise Windows and Linux servers. 
  - On these servers, you need to ensure you install the Microsoft Monitoring agent. 
  - This service also helps detect and prevent threats at an Infrastructure layer 
- Azure AD Identity Protection 
  - This is a service that can help detect suspicious actions related to user identities 
  - This helps add more security to the sign-ins to your Azure AD Account. 
  - This service can help detect the following
  - Users with leaked credentials
  - Sign-ins from anonymous IP addresses
  - Sign-ins from infected devices
  - Sign-ins from IP addresses with suspicious activity
  - Sign-ins from unfamiliar locations
  - Impossible travel to atypical locations
- Azure Firewall
  - This is a managed, cloud-based network security service that can be used to protect your network resources.
  - It has features such as Threat intelligence 
  - This can filter incoming requests and alert or deny traffic from/to malicious IP addresses and domains.
  - The firewall itself has built-in high availability.
  - It can scale automatically based on network traffic flows.
  - Here you can ensure that all traffic from machines in an Azure virtual network flows via the Azure Firewall service.
- Azure DDoS protection
  - This service helps protect against Distributed denial of service attacks.
  - This is probably the biggest security concern for companies when they expose their applications to the Internet.
  - You have 2 plans for Azure DDoS protection.
  - Basic – This is automatically enabled. This continuously monitors traffic in real time and looks at mitigation of common network-level attacks.
  - Standard – This is a paid plan. But you get many benefits
  - Here you can get real time attack metrics and diagnostic logs via Azure Monitor
  - You can get help from DDoS Experts during a live attack
- Azure Information protection
  - This is a solution that can help an organization classify and protect its documents and email by applying labels.
  - The labels can be applied automatically by administrators through the use of rules and conditions.
  - The labels can use visual markers on documents to tell the user the classification of the document
- Azure Advanced Threat Protection
  - This is a cloud-based security tool that can be used to identify, detect and investigate advanced threats, compromised identities.
  - This service can be used to protect identities and credentials stored in Active Directory.
  - When monitoring your on-premise Active Directory domain controllers, you need to install an Azure ATP sensor on the domain controller.
  - It can be used to identify and investigate suspicious user activities and advanced attacks.
- Azure Key Vault
  - Helps you perform Secrets management – Here you can securely store your tokens, passwords , certificates , API keys and other secrets
  - You can use this service to create encryption keys. You can then use these encryption keys to encrypt your data.
  - You can also easily provision, manage, and deploy public and private Secure Sockets Layer/Transport Layer Security (SSL/TLS) certificates
  - All the secrets and keys are safeguarded by Azure, using industry-standard algorithms, key lengths, and hardware security modules (HSMs).
  - You can also monitor all the key vault activity by enabling logging. The logs can be sent to an Azure storage account, to an event hub or to Azure Monitor logs.
- Azure Policies
  - This service can be used to create, assign and manage policies.
  - You can use these policies to ensure that resources in your Azure account remain compliant with corporate standards and service level agreements.
  - You can use in-built policies or even define your own policies
- Role-based access control
  - This can be used to assign access to resources in Azure.
  - For example if you wanted to give access to a user to manage virtual machines in your subscription, you can use role based access control
  - Roles can be accessed at different scopes - Subscription, Resource groups and resources
  - Reference - https://docs.microsoft.com/en-us/azure/role-based-access-control/overview
- describe the Cloud Adoption Framework for Azure
  - Helps you accomplish your goal of adopting azure by showing you relevant articles to read 
  - Use Total cost of ownership calculator to know costs
  - TCO calculator - https://azure.microsoft.com/en-us/pricing/tco/calculator/
  - Budget alerts helps you stay within budget
#### Describe privacy and compliance resources

- describe the Microsoft core tenets of Security, Privacy, and Compliance
- describe the purpose of the Microsoft Privacy Statement, Product Terms site, and Data Protection Addendum (DPA)
- describe the purpose of the Trust Center
- describe the purpose of the Azure compliance documentation
- describe the purpose of Azure Sovereign Regions (Azure Government cloud services and Azure China cloud services)


### Describe Azure cost management and Service Level Agreements (10- 15%)

#### Describe methods for planning and managing costs
- identify factors that can affect costs (resource types, services, locations, ingress and egress traffic)
- identify factors that can reduce costs (reserved instances, reserved capacity, hybrid use benefit, spot pricing)
- describe the functionality and usage of the Pricing calculator and the Total Cost of Ownership (TCO) calculator
- describe the functionality and usage of Azure Cost Management

#### Describe Azure Service Level Agreements (SLAs) and service lifecycles
- describe the purpose of an Azure Service Level Agreement (SLA)
  - describes Microsoft's commitments for uptime and connectivity
  - Different services have different SLAs.
- identify actions that can impact an SLA (i.e. Availability Zones)
- describe the service lifecycle in Azure (Public Preview and General Availability)
  - NO SLA on preview products
  - Private preview vs public preview
  - Private preview: request Microsoft to preview and give the feedback
  - Public preview
    - For services in public preview , you can actually view them from the Azure portal itself. These services are available for review for all customers.
- Recovery time objective RTO: maximum acceptable time an application is unavailable after an incident
- Recovery point objective RPO: maximum duration of data loss that's acceptable during a disaster

#### Azure support plans
- Basic support plan ( takes long time to resolve  )
- Developer ( use for non-prod)
- Standard (Fast response) (use for production workload) (24/7 email and phone)
- Professional Direct ( use for Business critical)
- [https://azure.microsoft.com/en-us/support/plans/](https://azure.microsoft.com/en-us/support/plans/)

### General
- There are two ways a VM can be stopped, resulting into two states from a cost viewpoint:
- Azure’s stopped state: An administrator or a process running on the OS in the VM shuts down the OS. In most cases, the administrator or a subscription co-administrator controls when this happens. As part of managing the VM, an administrator may need to manually shut down the OS temporarily (for example, to reconfigure an application running on the VM). However, administrators may also want to run other tools that shut down the OS (for example, Sysprep on a Windows VM). The OS in the VM is stopped, and the VM services are unavailable, but the VM continues to reserve the compute and network resources that Azure provisioned, and these resources will continue to incur charges.
- Azure’s deallocated state: Azure shuts down the VM by using Azure tools or processes. In most cases, the administrator or a subscription co-administrator controls when this happens. If the VM does not need to be used immediately but needs to remain in a resumable state, administrators can minimize costs by shutting down the VM using the Azure portal. When a VM is deallocated, the VM’s OS stops, and this frees up the hardware and network resources Azure previously provisioned for it.
- Reference(s): https://blogs.technet.microsoft.com/uspartner_ts2team/2014/10/10/azure-virtual-machines-stopping-versus-stopping-deallocating/

- What are **Azure Reservations**? Azure Reservations help you save money by committing to one-year or three-year plans for multiple products. Committing allows you to get a discount on the resources you use. Reservations can significantly reduce your resource costs by up to 72% from pay-as-you-go prices. Reservations provide a billing discount and don't affect the runtime state of your resources. After you purchase a reservation, the discount automatically applies to matching resources

- **Azure Logic Apps** is a cloud service that is designed to schedule, automate, and orchestrate tasks, business processes, and workflows to integrate apps, data, systems, and services across enterprises or organizations. 
  - Logic Apps simplifies app integration, data integration, system integration, enterprise application integration (EAI), and business-to-business (B2B) communication, whether in the cloud, on premises, or both. For example, the following are just a few workloads that can be automated with Logic Apps:
  - Process and route orders across on-premises systems and cloud services
  - Send email notifications with Microsoft 365 when events happen in various systems, apps, and services
  - Move uploaded files from an SFTP or FTP server to Azure Storage
  - Monitor tweets for a specific subject, analyze the sentiment, and create alerts or tasks for items that need review.
    - Reference(s): https://docs.microsoft.com/en-us/azure/logic-apps/logic-apps-overview

- **Azure Resource Manager (ARM)** is the deployment and management service for Azure. It provides a management layer that enables organizations to create, update, and delete resources in their Azure accounts. It offers management features such as access control, locks, and tags to secure and organize resources after deployment.
  - Reference(s): https://docs.microsoft.com/en-us/azure/azure-resource-manager/management/overview

- **Azure Kubernetes Service** (AKS) makes it simple to deploy a managed Kubernetes cluster in Azure. AKS reduces the complexity and operational overhead of managing Kubernetes by offloading much of that responsibility to Azure. For a hosted Kubernetes service, Azure handles critical tasks such as health monitoring and maintenance. The Kubernetes masters are managed by Azure. Users only manage and maintain the agent nodes.
  - Reference(s): https://docs.microsoft.com/en-us/azure/aks/intro-kubernetes

- **Microsoft Azure Sentinel** is a scalable cloud-native security information event management (SIEM) and security orchestration automated response (SOAR) solution. Azure Sentinel delivers intelligent security analytics and threat intelligence across the enterprise, providing a single solution for alert detection, threat visibility, proactive hunting, and threat response.
  - Azure Sentinel provides a bird’s-eye view across the enterprise, alleviating the stress of increasingly sophisticated attacks, increasing volumes of alerts, and long resolution timeframes. It allows you to do the following:
  - Collect data at cloud scale across all users, devices, applications, and infrastructure, both on premises and in multiple clouds
  - Detect previously undetected threats and minimize false positives using Microsoft's analytics and unparalleled threat intelligence
  - Investigate threats with artificial intelligence and hunt for suspicious activities at scale, tapping into years of cybersecurity work at Microsoft
  - Respond to incidents rapidly with built-in orchestration and automation of common tasks
  - Reference(s): https://docs.microsoft.com/en-us/azure/sentinel/overview

- Azure Trust Center was launched with the goal of providing customers and partners with easier access to regulatory compliance information.
- Reference(s): https://www.microsoft.com/en/trust-center/product-overview
- https://azure.microsoft.com/en-us/overview/trusted-cloud/

- Microsoft uses a wide variety of physical, infrastructure, and operational controls to help secure Azure—but there are additional actions you need to take to help safeguard your workloads. Turn on Security Center to quickly strengthen your security posture and protect against threats. Security Center offers posture management for your cloud workloads and enhanced threat protection with the Security Center Standard tier.
- Reference: https://azure.microsoft.com/en-us/services/security-center/ 


- To create or delete management locks, the following actions are necessary:
  - Microsoft.Authorization/*
  - Microsoft.Authorization/locks/*
    - Of the built-in roles, only Owner and User Access Administrator are granted these actions.
    - Reference(s): https://docs.microsoft.com/en-us/azure/azure-resource-manager/management/lock-resources

- **Azure network security groups** can be used to filter network traffic to and from Azure resources in an Azure virtual network. 
  - A network security group contains security rules that allow or deny inbound network traffic to or outbound network traffic from several types of Azure resources.
  - For each rule, a source, destination, port, and protocol can be specified.
  - Reference(s): https://docs.microsoft.com/en-us/azure/virtual-network/security-overview

- **Azure China** has distinct pricing and requires an account separate from an Azure global account. Microsoft Azure operated by 21Vianet (Azure China) is a physically separate instance of cloud services located in China. It is independently operated and transacted by Shanghai Blue Cloud Technology Co., Ltd., a wholly owned subsidiary of Beijing 21Vianet Broadband Data Center Co., Ltd. Any customer data on Azure China stays within China.
  - Reference(s): https://azure.microsoft.com/en-us/global-infrastructure/china/

- **Azure Policy** helps enforce organizational standards and assess compliance at scale. The compliance dashboard in Azure Policy provides an aggregated view that enables the evaluation of the overall state of the environment. In addition, viewers can drill down to each resource and  policy granularly. Azure Policy can help bring existing resources into compliance through bulk remediation and automatic remediation for new resources. Common use cases for Azure Policy include implementing governance for resource consistency, regulatory compliance, security, cost, and management. Policy definitions for these common use cases are available in the Azure environment as built-ins to help you get started.
- Reference(s): https://docs.microsoft.com/en-us/azure/governance/policy/overview

#### Links:
- https://docs.microsoft.com/en-us/azure/cloud-adoption-framework/ready/considerations/fundamental-concepts
- https://docs.microsoft.com/en-us/azure/governance/blueprints/overview
- Some notes are from course: https://www.udemy.com/course/microsoft-azure-beginners-guide