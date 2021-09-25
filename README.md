## Notes for [Exam AZ-900: Microsoft Azure Fundamentals](https://docs.microsoft.com/en-us/learn/certifications/azure-fundamentals/)

## Syllabus as of 9/25/21

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
- describe serverless computing
  - User only uses or pays for compute time when needed without deploying any compute resources
- describe Software-as-a-Service (SaaS)
  - User only uses the software without worrying about underlying details. e.g. gmail
- identify a service type based on a use case

#### Describe the differences between types of cloud computing

- define cloud computing
- describe Public cloud
- describe Private cloud
- describe Hybrid cloud
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
- describe the benefits and usage of Container (Blob) Storage, Disk Storage, File Storage, and storage tiers
- describe the benefits and usage of Cosmos DB, Azure SQL Database, Azure Database for MySQL, Azure Database for PostgreSQL, and SQL Managed Instance
- describe the benefits and usage of Azure Marketplace

### Describe core solutions and management tools on Azure (10-15%)

#### Describe core solutions available in Azure

- describe the benefits and usage of Internet of Things (IoT) Hub, IoT Central, and Azure Sphere
- describe the benefits and usage of Azure Synapse Analytics, HDInsight, and Azure Databricks
- describe the benefits and usage of Azure Machine Learning, Cognitive Services and Azure Bot Service
- describe the benefits and usage of serverless computing solutions that include Azure Functions and Logic Apps
- describe the benefits and usage of Azure DevOps, GitHub, GitHub Actions, and Azure DevTest Labs

#### Describe Azure management tools

- describe the functionality and usage of the Azure Portal, Azure PowerShell, Azure CLI, Cloud Shell, and Azure Mobile App
- describe the functionality and usage of Azure Advisor
- describe the functionality and usage of Azure Resource Manager (ARM) templates

- describe the functionality and usage of Azure Monitor
- describe the functionality and usage of Azure Service Health

### Describe general security and network security features (10-15%)

#### Describe Azure security features

- describe basic features of Azure Security Center, including policy compliance, security alerts, secure score, and resource hygiene
- describe the functionality and usage of Key Vault
- describe the functionality and usage of Azure Sentinel
- describe the functionality and usage of Azure Dedicated Hosts

#### Describe Azure network security

- describe the concept of defense in depth
- describe the functionality and usage of Network Security Groups (NSG)
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
- describe the functionality and usage of resource locks
- describe the functionality and usage of tags
  - maximum of 50 tag name/value pairs are allowed
- describe the functionality and usage of Azure Policy
- describe the functionality and usage of Azure Blueprints
- describe the Cloud Adoption Framework for Azure

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
- Recovery time objective RTO: maximum acceptable time an application is unavailable after an incident
- Recovery point objective RPO: maximum duration of data loss that's acceptable during a disaster

### Links:
- https://docs.microsoft.com/en-us/azure/cloud-adoption-framework/ready/considerations/fundamental-concepts