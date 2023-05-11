# Timed Mode

Platform as a Service (PaaS) solutions
- Azure App Service
- Azure SQL Databases
- Azure Storage accounts




A `VPN gateway` is a specific type of `virtual network gateway` that is used to send encrypted traffic between an Azure virtual network and an on-premises location `over the public Internet`.
- ** `Each virtual network` can have `only one VPN gateway`. 
- However, you can create `multiple connections to the same VPN gateway`. 
- When you create multiple connections to the same VPN gateway, all VPN tunnels share the available gateway bandwidth.

A `virtual network gateway` is composed of `two or more VMs` that are deployed to `a specific subnet` you create called `the gateway subnet`. 
- `Virtual network gateway VMs` contain `routing tables` and run specific `gateway services`. 
  - These VMs are created when you create a virtual network gateway.

There are various configurations available for your VPN gateway connections. 

- `Site-to-Site` VPN gateway connection 
  - is used to connect your on-premises network to an Azure virtual network over an IPsec/IKE (IKEv1 or IKEv2) VPN tunnel.
  - This type of connection `requires a VPN device located on-premises` that has an externally facing public IP address assigned to it.

- `Point-to-Site (P2S)` VPN gateway connection
  - allows you to create a secure connection to your virtual network `from an individual client computer`.
  - A P2S connection is established by `starting it from the client’s computer`.
  - P2S VPN is also a useful solution to use instead of S2S VPN when you have only `a few clients` that need to connect to a VNet.




`VNet peering connection`
- this connection type simply provides a low-latency, high-bandwidth connection between resources in different Azure virtual networks. 




`ExpressRoute connection`
- Using `ExpressRoute`, the connectivity can be from an any-to-any (IP VPN) network, a point-to-point Ethernet network, or a virtual cross-connection `through a connectivity provider at a co-location facility`. 
- `ExpressRoute` connections `do not go over the public Internet`, unlike an IPsec/IKE (IKEv1 or IKEv2) VPN tunnel.



Azure RBAC Roles
- The `Owner role` lets you manage everything, including access to resources and the contributor’s role. It grants you full access to manage all resources, including `the ability to assign roles in Azure RBAC`.

- The `Contributor role` grants you full access to manage all resources but does `not allow you to assign roles in Azure RBAC`.

- The `Reader role` lets you view everything, but not make any changes.

- ** `Virtual Machine Contributor role` lets you `manage virtual machines`, but `not access to them`, and `not the virtual network or storage account` they’re connected to.




Azure Reservations
- help you save money by committing to one-year or three-year plans for multiple products.
- After you purchase a reservation, the discount `automatically applies` to `matching resources`.

- ** A `reserved capacity` is different from a `reserved instance`.

  - A `reserved capacity` is mainly used for `Azure database services` such as Azure SQL Database, Azure Cosmos DB, Azure Synapse Analytics, and Azure Cache for Redis. 
    - NOTE: If the scenario stated that the company will migrate to a new instance, it is not a reserved capacity.

  - A `reserved instance` has a one-year or three-year term on `Windows and Linux virtual machines`. 




Azure Key Vault
- this is a service that enables Azure subscribers to `safeguard and control cryptographic keys` and other secrets used by cloud apps and services.




Microsoft Defender for `Cloud`
- this is just a unified infrastructure `security management system` that strengthens the security posture of `your data centers` and provides `advanced threat protection` across `your hybrid workloads in the cloud`.

- Defender for Cloud provides the tools needed to `harden your resources`, `track your security posture`, `protect against cyberattacks`, and `streamline security management`.

- Defender for Cloud collects, analyzes, and integrates log data from your Azure resources, the network, and connected partner solutions, such as firewalls and endpoint agents. Defender for Cloud uses the log data to detect real threats and reduce false positives. 

- A list of prioritized security alerts is shown in Defender for Cloud, along with the information you need to quickly investigate the problem and steps to take to remediate an attack.

- allows you to investigate and respond to `a security alert`.

- it can protect workloads running in `Azure, on-premises, and multicloud` (Amazon AWS and Google GCP) resources. ** NOT just Azure.

- in order to be able to utilize the `advanced` security management and threat detection capabilities, you must `enable enhanced security features` in your Microsoft Defender for Cloud plan. ** It is NOT enabled by default.







** Microsoft Defender for `Identity` (formerly Azure Advanced Threat Protection, also known as Azure ATP)

- is `a cloud-based security solution` that leverages `your on-premises Active Directory signals` to identify, detect, and investigate advanced threats, compromised identities, and malicious insider actions directed `at your organization`.

- Directly monitor `the domain controller traffic` and `detect security threats` using `a sensor`
  
  - `Microsoft Defender for Identity` monitors your domain controllers by capturing and parsing network traffic and leveraging Windows events directly from your domain controllers, then analyzes the data for attacks and threats. Utilizing profiling, deterministic detection, machine learning, and behavioral algorithms, Defender for Identity learns about your network, enables detection of anomalies, and warns you of suspicious activities.
  
  - `Microsoft Defender for Identity sensor` is installed directly on your domain controller. It accesses the event logs from the domain controller to collect the required information. After the logs and network traffic are parsed by the sensor, Defender for Identity sends only the parsed information to the Defender for Identity cloud service (only a percentage of the logs are sent).





NOTE: Deploying virtual machines to `a scale set` ensure that if a single data center fails, the application will not be affected. (`Scale set` can also specify to distribute VM across availability zones as well. Not just `availability set`)

Difference between `Scale Sets` and `Availability Sets`

- VM `Availability Set`
  - `a set of discrete VMs` which have their own names and individual properties, 
  - but are spread across fault domains, which means when you have `more than one VM in a set` it reduces the chances of losing all your VMs in event of a hardware failure in the host or rack.
  - ** We can use `an availability set` when you have `a predictable workload` that you want to `protect against downtime`. 
    - In other words, if you know your solution can run on `a single VM`, you would create `two VMs in an availability set` to ensure that at least one VM is running at all times, and `a load balancer` to route traffic to `an active VM`.
    - ** So, you can use `availability set` to configure `the number of zones` in which your application can run.
  - Azure availability set is `a logical grouping capability` that ensures the VMs you place within an Availability Set run across multiple physical servers, compute racks, storage units, and network switches.
    - If a hardware or software failure happens, only a subset of your VMs are impacted and your overall solution stays operational.

- VM `Scale set` consists of `a set of identically configured VMs`, 
  - lets you create and manage a group of load-balanced VMs.
  - also spread across fault domains (in fact a scale set is an implicit availability set with 5 fault domains).
  - In scale sets, being identical, make it `very easy to add or remove VMs` from the set while preserving `high availability`, which in turn makes it easy to implement `autoscale`, and to perform operations on the whole set or a subset of VMs. 
  - ** We can use `scale sets` when the workload on your solution changes a lot or is unpredictable (need auto-scaling). For example, if you have a solution that normally works using only one VM, but may need up to 5 VMs to work under heavy demand, you would use a scale set to ensure that your solution quickly scales to demand.
    - ** So, you can use scale set to configure `the number of instances` that a given application can run on

References
- https://medium.com/awesome-azure/difference-between-scale-set-and-availability-set-in-azure-9b2da03b891c
- https://tutorialsdojo.com/azure-scale-set-vs-availability-set/




Difference between `Azure Load Balancer` and `Application Gateway`
- `Azure Load Balancer` works with traffic at `Layer 4` `(TCP/UDP)`.
  - The backend pool instances can be Azure Virtual Machines or instances in a virtual machine scale set.
  - A `public load balancer` can provide outbound connections for virtual machines (VMs) inside your virtual network. 
    - Public Load Balancers are used to load balance `internet traffic to your VMs`.
    - These connections are accomplished by translating their private IP addresses to public IP addresses.
  - An `internal (or private) load balancer` 
    - Internal load balancers are used to load balance `traffic inside a virtual network`.
    - is used where private IPs are needed at the frontend only.  
    - A load balancer frontend can be accessed from `an on-premises network` in `a hybrid scenario`.

- `Application Gateway` works with `Layer 7` traffic, and specifically with `HTTP/S (including WebSockets)`.
  - NOTE: `Application Gateway` ~ `Amazon ALB`

References
- https://medium.com/awesome-azure/azure-difference-between-azure-load-balancer-and-application-gateway-9a6019c23840




Azure Spot Virtual Machine
- are unused compute capacity at `deep discounts`.
-  If your workload `can tolerate interruptions` and its execution time is flexible, then using spot VMs can significantly reduce the cost of running your workload in Azure. 
- ** Take note that it’s stated in the scenario that `“the application is processing mission-critical workloads.”` >> This means that the application instance `must be uninterruptible`.
  - ** So, in `mission-critical workloads`, use `Azure Reservations` to reduce costs instead.




Reliability <> High availability

- A reliable workload is one that is `both resilient and available`. 
  
  - `Resiliency` is the ability of the system to `recover from failures and continue to function`.
    - The goal of resiliency is to return the application to a fully functioning state after a failure occurs. 
    
  - `Availability` is whether your users can access your workload when they need to.




Azure virtual machines are `billed by the second` and `NOT per hour`.


** If you `delete an Azure virtual machine` >> `Any disks that are attached` to the VM will actually `NOT be deleted` if its VM is deleted. 
  - This underlying mechanism helps to `prevent data loss` due to the unintentional deletion of VMs. 
  - Take note that after a VM is deleted, you will still `continue to pay for unattached disks`.


** `Disks attached` to `stopped virtual machines` do still incur costs




** You can use `Azure Portal, Azure CLI, and Azure PowerShell` on all platforms: Windows, Mac OS, Linux.

NOTE: `Azure PowerShell` is a module that you can install for `Windows PowerShell` or `PowerShell Core`, 
- ** `PowerShell Core` is a cross-platform version of PowerShell that runs on Windows, Linux, or macOS. 
- Azure PowerShell enables you to connect to your Azure subscription and manage resources. Windows PowerShell and PowerShell Core provide services such as the shell window and command parsing.




Take note of the following restrictions in creating `a virtual network`:
- Virtual networks with `overlapping address space cannot peer`. If you intend to peer these virtual networks, they must have unique address spaces.

- Virtual networks `can’t have the same name` if they are located `in the same resource group`.

- Virtual networks `in a resource group can’t communicate with each other by default`. You can connect a virtual network to other virtual networks using `virtual network peering` or `to your on-premises network` using `an Azure VPN gateway`.




Azure Hybrid Benefit
- For customers with `Software Assurance`, `Azure Hybrid Benefit for Windows Server` allows you to use `your on-premises Windows Server licenses` and run Windows virtual machines on Azure at a reduced cost. 
- ** You `only pay for the compute costs` of a Windows virtual machine, not including license cost because you already pay it on-premises.




`Recommended Region` is simply a region that provides `the broadest range of service capabilities and is designed to support Availability Zones`. 
- These are designated in the Azure portal as Recommended.
- NOTE: `Region` <> `Recommended Region`



`Geography` is an area of the world containing `at least one Azure region`. 
- Geographies are fault-tolerant to withstand `complete region failure` through their connection to our dedicated high-capacity networking infrastructure.


`Region` contains `multiple availability zones`, with `each zone made up of one or more data centers` that are connected through `a dedicated regional low-latency network`.


An `Availability Zone` is a high-availability offering that protects your applications and data from datacenter failures. 
- Each zone is made up of `one or more data centers` equipped with independent power, cooling, and networking.




`Resource Group` is a logical container that you use to group related resources in a subscription.
- Each resource can exist in only one resource group.
- Resource groups CAN span `multiple regions`.
- Resources can connect to other resources located in `another resource group`.
- You can add or remove a resource to a resource group at any time.
- Azure resource groups are `regional in scope` but `can contain Azure resources that span to multiple regions`.


`Azure Blob` = Object store for text and binary data.
`Azure Table` = Structured NoSQL data in the cloud.
* `Azure Disks` = Block-level storage volumes.
* `Azure Files` = Shard access that utilizes Server Message Block (SMB) protocol.




`Capital Expenditures or CapEx` is defined as funds used allocated by organizations to obtain, upgrade, and maintain physical assets that are `paid upfront`, such as data centers. 
- This expenditure model is `an upfront spending` of money on physical infrastructure.

`Operating Expenditures or OpEx` is defined as funds that are used by organizations for their day-to-day operations. Think of OpEx as your electricity and water bill. 
- The more you use, the higher the charges.
- ** Azure on-demand or pay-as-you-go pricing is an example of an OpEx model.




`Application Security Group` (ASG) vs `Network Security Group` (NSG)


`Network security group` ~ Amazon NACL + Security Group
- Network Security Group is the Azure Resource that you will use to enforce and control the network traffic with.
- is used to filter network traffic to and from Azure resources in an Azure virtual network.
- A network security group contains security rules that allow or deny inbound network traffic to, or outbound network traffic from, several types of Azure resources. 
  - For each rule, you can specify source and destination, port, and protocol.
- They can be applied either on a virtual machine or subnet (one NSG can be applied to multiple subnets or virtual machines):-




`Application Security Group` >> In Virtual Network level (across subnets)
- Application Security Group is an object reference within a Network Security Group.
  - An application security group is `a logical collection of virtual machines (NICs)`. You join virtual machines to the application security group, and then use the application security group `as a source or destination in NSG rules`.

- ASGs are used within a NSG to apply a network security rule to a specific workload or group of VMs
  - defined by ASG worked as being the "network object" & expilicit IP addresses are added to this object. 

- allow us to define fine-grained network security policies based on `workloads, centralized on applications`, `instead of explicit IP addresses` like NSG.
  - In other words, this is primarily used to configure network security as a natural extension of an application’s structure, without manual maintenance of explicit IP addresses.

- We can define a single collection of rules using ASGs and NSGs. We just have to apply a single NSG to our entire virtual network on all subnets.
- If the VM is running more than one workloads, we can simply assign multiple ASGs.

- Another great use of this is for scalability, creating the virtual machine and assigning the newly created virtual machine to its ASG will provide it with all the NSG rules in place for that specific ASG - zero distribution to your service!

** So, if you want to modify your Network Security Group to allow the traffic to the specific IP address like "Your colleague is working on a project and informed you that he needs RDP access to the server hosted on Azure. He gave you his workstation’s IP address." >> whitelist his IP address on `Network Security Group` NOT `Application Security Group`.

References
- https://medium.com/awesome-azure/azure-application-security-group-asg-1e5e2e5321c3
- https://www.websitebuilderinsider.com/what-is-difference-between-nsg-and-asg-azure/
- https://www.kainos.com/insights/blogs/microsoft-azure-nsgs-asgs-simplified
- https://tutorialsdojo.com/network-security-group-nsg-vs-application-security-group/





Azure virtual network TAP (Terminal Access Point)
- this just allows you to continuously stream your virtual machine network traffic to a network packet collector or analytics tool.




Azure ExpressRoute connection
- is primarily used to create private connections between Azure and your on-premises network or in a colocation environment.




Network security group
- simply provides a distributed network layer traffic filtering to limit traffic to resources `within virtual networks in each subscription`.
  - ** For across multiple virtual networks and subscriptions >> Use `Azure Firewall` instead



Azure Firewall
- is `a fully stateful, centralized network firewall as-a-service`, which provides network- and application-level protection `across different subscriptions and virtual networks`.
- Ex. limit the amount of outbound HTTPS traffic to a specified list of fully qualified domain names (FQDN) as well as limit the inbound traffic to the virtual networks for hundreds VMs across multiple virtual networks and subscriptions.




Azure Files ~ EFS
- as a document sharing solution that you can map or mount in your on-premises Windows servers.
- enables you to set up highly available `network file shares` that can be accessed by using the standard `Server Message Block (SMB) protocol`. 
  - That means that multiple VMs can share the same files with both read and write access.
- ** This `CAN be mounted to your on-premises servers`



Azure Cosmos DB
- this service is Microsoft’s globally distributed, multi-model database service for mission-critical applications.
- Fast, distributed `NoSQL and relational database` at any scale
- `a fully managed` and `serverless` distributed database supporting open-source `PostgreSQL`, `MongoDB`, and `Apache Cassandra`.




Azure Managed Disks ~ EBS
- these are block-level storage volumes that are managed by Azure and used with Azure Virtual Machines.
- Managed disks are like `a physical disk in an on-premises server` but virtualized. 
- ** However, this `CANNOT be mounted to your on-premises servers`, unlike `Azure Files`.



Azure Blob storage ~ S3
- is `an object storage solution` for the cloud. 
- Blob storage is optimized for storing massive amounts of unstructured data, such as text or binary data. 
- Objects in Blob storage can be accessed from anywhere in the world via `HTTP or HTTPS`. 
- ** You `CANNOT mount this to your on-premises servers`.




NOTE: `Subnet` and `Network interface` can be attached to the `network security group`
- Unless you have a specific reason to, it is recommended that you associate a network security group to a subnet or a network interface, `but not both`. 
  - Since rules in a network security group associated with a subnet `can conflict` with rules in a network security group associated with a network interface, you can have unexpected communication problems that require troubleshooting.

NOTE: You CANNOT attach `Virtual Network` to the `network security group`.


Azure Cost Management + Billing
- ** CAN provides `recommendations` on how you can optimize and improve the efficiency of your workloads by `identifying idle and underutilized resources`.

You use Azure Cost Management + Billing features to:
– Conduct billing administrative tasks such as `paying your bill`
– Manage billing access to costs
– Download `cost and usage data` that was used to generate `your monthly invoice`
– ** Proactively apply `data analysis` to your costs
– Set spending thresholds
– ** Identify opportunities for workload changes that can `optimize your spending`




To ensure that your Azure environment adheres to the regional compliance requirements of the company
- Use `Microsoft Service Trust Portal`

The `Microsoft Service Trust Portal` is a portal that provides access to various content, tools, and other resources about `Microsoft security, privacy, and compliance practices`.
- The `Service Trust Portal` contains details about `Microsoft’s implementation` of controls and processes that protect our cloud services and the customer data therein.
-  this is simply `Microsoft’s public site` for publishing `audit reports` and `other compliance-related information` associated with `Microsoft’s cloud services`.




Azure Advisor
- this is simply a personalized cloud consultant that helps you follow best practices to optimize your Azure deployments.



Azure Marketplace
- is only a channel to market and sell your cloud solutions that are certified to run on Azure.




Azure Key Vault
- is a tool for securely storing and accessing `secrets`
  - So, it is used to `create and store TLS/SSL certificates`.
- `A secret` is anything that you want to tightly control access to, such as `API keys`, `passwords`, or `certificates`.
- `A vault` is `a logical group of secrets`.




Azure Artifacts
- This is primarily used to create and share `Maven`, `npm`, and `NuGet` package feeds `from public and private sources`.




Azure Policy 
- helps to `enforce organizational standards` and to `assess compliance` at scale.
- Policy evaluates resources in Azure by `comparing the properties of resources` to the `business rules`. 
  - These `business rules`, described in JSON format, are known as `policy definitions`. 
  - To simplify management, `several business rules can be grouped together` to form `a policy initiative`.
- Once your business rules have been formed, the policy definition or initiative is assigned to any scope of resources that Azure supports, such as management groups, subscriptions, resource groups, or individual resources. 

Example usage of `Azure Policy`
- automatically block `new` network security group security rules that `contains port 22, 80 and 3389`.




Azure Resource Manager
- it is used for the deployment and management service for Azure.
- it provides `a management layer` that enables you to create, update, and delete resources in your Azure account.
- You use management features, like `access control`, `locks`, and `tags`, to secure and organize your resources after deployment.




Microsoft Defender for Cloud 
- is a tool for security `posture` management and threat protection. 
- It strengthens the security `posture` of your cloud resources, and with its integrated Microsoft Defender plans, Defender for Cloud protects workloads running in Azure, hybrid, and other cloud platforms.





Azure Blueprints
- This simply defines `a repeatable set of Azure resources` that implement and adhere to your organization’s standards, patterns, and requirements and rapidly build new environments with a set of built-in components to speed up development and delivery.





Q: You need to recommend a solution to `migrate the users the quickest way to Azure Active Directory` with minimal impact on users.
A: Sync the on-premises Active Directory to Azure Active Directory using `AD connect`.

`Azure AD Connect` installs an on-premises service that `orchestrates synchronization between your on-premises Active Directory and Azure Active Directory`. 




Azure storage account
- An Azure storage account contains all of your Azure Storage data objects: blobs, files, queues, tables, and disks.
- The storage account provides a unique namespace for your Azure Storage data that is accessible from anywhere in the world over HTTP or HTTPS.

- ** Data in an Azure Storage account is always replicated three times in the primary region.

  - `LRS` = 3 copies within a single region.

  - `ZRS` = 3 copies `across separate AZs` within a single region.

  - `Geo-redundant storage (GRS)` copies your data `synchronously` three times within `a single physical location in the primary region` using `LRS`.
    - It then copies your data `asynchronously` to `a single physical location in a secondary region` that is hundreds of miles away from the primary region.
    - To sum, 6 copies total, 3 in primary region and other 3 in secondary region.

  - `Geo-zone-redundant storage (GZRS)` copies your data `synchronously` `across three Azure availability zones in the primary region` using `ZRS`. 
    - It then copies your data `asynchronously` to `a single physical location in the secondary region`.
    - ** Not cost effective because `geo-zone-redundant storage` is costlier than `geo-redundant storage`.
    - To sum, 6 copies total, 3 in `across separate AZs` primary region and other 3 in secondary region.

- NOTE: The primary difference between `GRS` and `GZRS` is how data is replicated in the primary region. 

- NOTE: `Within the secondary region`, data is always replicated `synchronously three times` using `LRS`. 
  - `LRS` in `the secondary region` protects your data against hardware failures.






Azure Resource Manager (ARM) templates ~ CloudFormation
- To implement infrastructure as code for your Azure solutions, use Azure Resource Manager (ARM) templates. 
- The template is a JavaScript Object Notation (JSON) file that defines the infrastructure and configuration for your project.
- The template uses declarative syntax, which lets you state what you intend to deploy without having to write the sequence of programming commands to create it.
- Ex. 
  - Used to automatically deploy the same set of servers to another region.




The data moving in and out of Azure data centers, as well as data moving between Azure data centers, is called `bandwidth`.

** Remember these concepts regarding data transfer:
- FREE
  - Data transfer `to Azure` is `always free`
    - ** EVEN Data inbound to Azure from an on-premises network over `ExpressRoute` is still `free`
  - Data transfer `within the same Availability Zone` is `free`
- NOT FREE
  - Data transfer `between Availability Zones` is `not free`
  - Data transfer `between Azure regions and to other continents` is `not free`
  - `outbound` data transfer from Azure is `charged at the normal rate`.




Resource group
- A resource group is a container that holds related resources for an Azure solution.
- The resource group stores `metadata about the resources`. 
  - Therefore, when you specify `a location for the resource group`, you are specifying `where that metadata is stored`.
- Resource groups are `free` but `resources inside` will have their corresponding `costs`.

- Remember these two important concepts about resource groups:
  - ** When you `delete a resource group`, `all resources` in the resource group are `also deleted`.
  - Azure resource groups are `regional in scope` but it `can contain Azure resources that span to multiple regions`.
  - `A resource group’s permission` will `be inherited` by the resources inside it.
  - When you assign `a tag to a resource group`, the resources within that group will `NOT inherit` the tag.



Azure Dedicated Host
- provides `physical servers` that are able to host one or more virtual machines `dedicated to a single customer`.



Azure Batch 
- this service only creates and manages `a pool of compute nodes (virtual machines)`, installs the applications you want to run, and `schedules jobs` to run on the nodes.

 


Azure Virtual Desktop
- lets you provision `Windows desktops` that can `host desktop applications` in just a few minutes, scale easily and allow users to connect with any device over the internet?
- Azure Virtual Desktop is `a desktop and application virtualization service` that runs on the cloud. 
- It enables your users to use `a cloud-hosted version of Windows from any location`. 
- Azure Virtual Desktop works `across devices` like Windows, Mac, iOS, Android, and Linux. 
  - It works with `apps` that you can use to access remote desktops and apps. 
  - You can also use most modern `browsers` to access Windows Virtual Desktop-hosted experiences.








** NOTE: You need to create or have `a subscription` FIRST to create resources on Azure.

To manage access and create Azure resources, you must have `the subscription` >> and then >> `create users with appropriate roles`. Azure has an authorization system called `Azure role-based access control (Azure RBAC)` with several built-in roles you can choose from.

`A subscription` is an agreement with Microsoft to use `one or more Microsoft cloud platforms or services`, for which charges accrue based on either `a per-user license fee` or on `cloud-based resource consumption`.

- `Microsoft’s Software as a Service (SaaS)-based` cloud offerings (`Microsoft 365` and `Dynamics 365`) charge `per-user license fees`.

- `Microsoft’s Platform as a Service (PaaS)` and `Infrastructure as a Service (IaaS)` cloud offerings (`Azure`) `charge based on cloud resource consumption`.

** NOTE: `Admin account` and `Tenant account`
- Even if you have these accounts, if you `do not have an Azure subscription`, you still `won’t be able to create resources`.





Q: You plan on migrating several virtual machines to Azure for your frontend and backend applications. There is a compliance requirement wherein the back-end servers must be on `a separate network segment`.
A: One `virtual network` each for frontend and backend servers

NOTE: Wrong >> One `network security group` each for frontend and backend servers




`Azure Virtual Network (VNet)` 
- is the fundamental building block for your private network in Azure. 
- VNet enables many types of Azure resources, such as Azure Virtual Machines (VM), to securely communicate with each other, the Internet, and on-premises networks.
- ** By default, virtual networks `CANNOT communicate with each other`.



Azure Container Instances ~ Fargate
- offers the fastest and simplest way to run a container in Azure, without having to manage any virtual machines and without having to adopt a higher-level service.



Azure Logic Apps ~ Step Functions
- helps you schedule, automate, and orchestrate tasks, business processes, and workflows when you need to integrate apps, data, systems, and services across enterprises or organizations.





`Consumption-based price`
- You are charged for only what you use. This model is also known as the `Pay-As-You-Go` rate.

`Fixed price`
- You provision resources and are charged for those instances whether or not they are used.



** NOTE: `Reservations` are `NOT` considered as `consumption-based pricing`
- When you purchase `reserved instances`, the resources are `no longer charged at the pay-as-you-go rates`.





NOTE: about `Platform as a service (PaaS) solution`
- A platform as a service (PaaS) solution provides the capability to `automatically scale` the platform without any manual intervention.
- A platform as a service (PaaS) solution provides `a framework that developers can build upon` to develop or customize cloud-based applications.

- ** WRONG >> A platform as a service (PaaS) solution provides `full control to the underlying operating systems of the Azure resources` that run the host applications
  - this is what an `Infrastructure as a Service (IaaS) solution` provides, `NOT a PaaS solution`.






Azure Advisor
- is a personalized cloud consultant that helps you follow best practices to optimize your Azure deployments. 
- It analyzes your resource configuration and usage telemetry and then recommends solutions that can help you improve:

  - `Reliability` (formerly called `High Availability`): To ensure and improve the `continuity of your business-critical applications`.

  - `Security`: To detect `threats and vulnerabilities` that might lead to security breaches.

  - `Performance`: To improve the `speed` of your applications.

  - `Cost`: To optimize and reduce your overall Azure `spending`.

  - `Operational Excellence`: To help you achieve `process and workflow efficiency`, `resource manageability`, and `deployment best practices`.


NOTE: Your `secure score` in `Microsoft Defender for Cloud` will `increase` if you remediate `all of the security recommendations` provided by `Azure Advisor`.

NOTE: `Azure Advisor` only provides `a list of Azure VMs that are NOT properly backed up` and `not the other way around`, meaning NOT provides a list of Azure virtual machines that are backed up by the Azure Backup service.

NOTE: `Azure Advisor` can only provide `limited security recommendations for Azure Active Directory`. 
- It is `NOT capable of calculating user risk levels` or providing `custom` Active Directory recommendations. 
  - These functions can only be provided by `Azure AD Identity Protection`.



Azure Traffic Manager
- is simply `a DNS-based traffic load balancer` that enables you to distribute traffic optimally to services `across global Azure regions` while providing high availability and responsiveness.
- ** However, you `CANNOT` use this to distribute traffic evenly to `virtual machines`. Use `Public/Private Load Balancer` instead.


Azure Front Door
- enables you to define, manage, and monitor the global routing for your web traffic by `optimizing performance` and `ensuring quick global failover` for high availability that works at `Layer 7 or HTTP/HTTPS layer`.



Azure AD Connect Health
- Help you monitor `your on-premises identity infrastructure` and ensure `a reliable connection to Office 365` and `Microsoft Online Services`.




Azure App Service 
- this only enables you to build and host web apps, mobile backends, and RESTful APIs in the programming language of your choice `without managing infrastructure`. 
- It offers `auto-scaling` and `high availability`, supports both Windows and Linux, and enables `automated deployments` from GitHub, Azure DevOps, or any Git repo.



Azure Application Gateway
- this service is simply `a web traffic load balancer` that enables you to manage traffic to your `web applications`.



Application Insights
- You can use it to monitor your live applications. 
- It will automatically detect performance anomalies and includes powerful analytics tools to help you diagnose issues and understand what users actually do with your app.




A Point-to-Site (P2S) VPN gateway connection
- lets you create a secure connection to your virtual network from an individual client computer. A P2S connection is established by starting it from the client computer. 
- This solution is useful for telecommuters who want to connect to Azure VNets from a remote location, such as from home or a conference. 
- P2S VPN is also a useful solution to use instead of S2S VPN when you have only a few clients that need to connect to a VNet.

To sum, You can set up `a Point-to-Site VPN connection` that uses `Internet Protocol Security (IPsec)` to connect to your `Azure virtual network` using `your home computer` via the `public Internet`.



Azure Firewall
- is just `a fully stateful firewall-as-a-service` that allows you to `centrally create, enforce, and log application and network connectivity policies` `across subscriptions` and `Azure virtual networks`.



`Zero Trust` = a security model that protects organizations by managing and granting access based on the `continual verification` of identities, devices and services.

`Zero Trust` = a security strategy. It is not a product or a service but `an approach in designing and implementing` the following set of security principles:
- Verify explicitly: Always authenticate and authorize based on `all available data points`.
- Use `least privilege acces`: Limit user access with Just-In-Time and Just-Enough-Access (JIT/JEA), risk-based adaptive policies, and data protection.
- `Assume breach`: Minimize blast radius and segment access. Verify end-to-end encryption and use analytics to get visibility, drive threat detection, and improve defenses.

** Instead of believing everything behind the corporate firewall is safe, the Zero Trust model `assumes breach` and verifies each request as though it originated from `an uncontrolled network`.
- Regardless of where the request originates or what resource it accesses, the Zero Trust model teaches us to `“never trust, always verify.”`




Service Trust Portal
- The Service Trust Portal is Microsoft’s public site for publishing audit reports and other compliance-related information associated with Microsoft’s cloud services.




Azure storage account
- An Azure storage account contains all of your Azure Storage data objects: `blobs, files, queues, tables, and disks`.
- The storage account provides `a unique namespace for your Azure Storage data` that is accessible from anywhere in the world over `HTTP or HTTPS`. 
- Data in your Azure storage account is `durable and highly available, secure, and massively scalable`.

Azure storage offers `different access tiers`, which allow you to store `blob object data` in the most cost-effective manner. The available access tiers include:

- `Hot` – Optimized for storing data that is `accessed frequently`.
  - has `higher storage costs` compared with `cool and archive tiers`.

- `Cool` – Optimized for storing data that is `infrequently accessed` and `stored for at least 30 days`.
  - this storage type still `costs higher than the archive tier`. 

- `Archive` – Optimized for storing data that is `rarely accessed` and `stored for at least 180 days` with flexible latency requirements (on the order of hours).




Azure DNS
- is `a hosting service for DNS domains` that provides name resolution by using Microsoft Azure infrastructure.
- By hosting your domains in Azure, you can manage your DNS records by using the same credentials, APIs, tools, and billing as your other Azure services.





Azure Resource Manager (ARM) ~ CloudFormation
- To implement `infrastructure as code` for your Azure solutions, use `Azure Resource Manager (ARM) templates`. 
  - The template is a `JavaScript Object Notation (JSON) file` that defines the infrastructure and configuration for your project. 
  - The template uses `declarative syntax`, which lets you state what you intend to deploy without having to write the sequence of programming commands to create it. 
  - In the template, you specify the `resources` to deploy and the `properties for those resources`.
  - ** ARM templates allows you to `export the templates`.
  - ** You can use `variables` to `simplify` your ARM template. 
    - Rather than repeating complicated expressions throughout your template, you define `a variable` that contains the complicated expression. 
    - Then, you use that variable as needed throughout your template.




** Scenario: A company has `a resource group` named TutorialsDojoRG and `an Azure virtual network` named TutorialsDojoVNET. `A new Azure policy` has been assigned to TutorialsDojoRG stipulating that `any virtual network resource type` is NOT allowed in the resource group. 

Ans: ** The existing TutorialsDojoVNET virtual network will `continue to work properly`.
- ** The existing TutorialsDojoVNET virtual network will `not be automatically deleted`. 
- *** Azure will just `tag` the existing virtual network as `a non-compliant resource`.

Reason:
- `Azure Policy` helps to enforce organizational standards and to assess compliance at-scale.
- It also helps to bring your resources to compliance through 
  - `bulk remediation` for `existing resources` and 
  - `automatic remediation` for `new resources`.

- Common use cases for Azure Policy include `implementing governance` for resource consistency, regulatory compliance, security, cost, and management.

- ** While these effects primarily affect a resource when the resource is `created or updated`, Azure Policy also supports dealing with `existing non-compliant resources` without needing to alter that resource.

- In this scenario, a company has a resource group named TutorialsDojoRG and an Azure virtual network named TutorialsDojoVNET. A new Azure policy has been assigned to TutorialsDojoRG stipulating that any virtual network resource type is not allowed in the resource group.

- With this new policy, a user will not be able to launch a new virtual network to the TutorialsDojoRG resource group. The existing TutorialsDojoVNET virtual network will be tagged as a non-compliant resource, but it will not be deleted or affected in any way.




Q: A company needs to configure its `Azure Active Directory` to `automatically prompt a user to change the password` if the user signs in from `an anonymous IP address`. Which Azure service should you use?
- Ans: `Azure Active Directory Identity Protection`





Azure AD Identity Protection
- is a tool that allows organizations to accomplish three key tasks:
  - Automate the detection and remediation of identity-based risks.
  - Investigate risks using data in the portal.
  - Export risk detection data to third-party utilities for further analysis.

- Identity Protection uses the learnings Microsoft has acquired from its position in organizations with Azure AD, the consumer space with Microsoft Accounts, and in gaming with Xbox to protect your users. Microsoft analyses 6.5 trillion signals per day to identify and protect customers from threats.

- The signals generated by and fed to Identity Protection can be further fed into tools like Conditional Access to make access decisions or fed back to a security information and event management (SIEM) tool for further investigation based on your organization’s enforced policies.

- ** You can detect `sign-ins that are made via anonymous IP addresses` using the Azure Identity Protection. `Signs in from an anonymous IP address` could originate from `a Tor browser` or `an anonymizer VPNs`.

- It can be exported to other tools for archive and further investigation and correlation. The Microsoft Graph-based APIs allow organizations to collect this data for further processing in a tool such as their SIEM.






Azure AD Privileged Identity Management
-  this just provides `a time-based and approval-based role activation` to `mitigate the risks` of excessive, unnecessary, or misused access permissions on resources that you care about. 



Microsoft Defender for Identity
- this is only `a cloud-based security solution` that leverages your `on-premises Active Directory signals` to identify, detect, and investigate `advanced threats, compromised identities, and malicious insider actions` directed at your organization.





NOTE: `Data` in `an Azure Storage account` is ALWAYS `replicated three times` in `the primary region`. Azure Storage offers four options for how your data is replicated:

- Locally redundant storage (LRS) = `3 copies` within a single region
  - ** copies your data `synchronously` `three times` within `a single physical location` in `the primary region`.
  - LRS is the `least expensive` replication option 
  - but is `NOT recommended` for applications requiring `high availability`.

- Zone-redundant storage (ZRS) = `3 copies` across separate AZs within a single region
  - ** copies your data `synchronousl`y across `three Azure availability zones` in `the primary region`.
  - For applications requiring `high availability`.

- Geo-redundant storage (GRS) = `6 copies` = `3 copies` within the primary region (LRS) + `3 copies` within the secondary region (LRS)
  - ** copies your data `synchronously` `three times` within `a single physical location` in `the primary region`.
    - >> Primary region duplication = `LRS`. 
  - ** It then copies your data `asynchronously` to `a single physical location` in `a secondary region` that is hundreds of miles away from the primary region.
    - >> Secondary region duplication ~ `LRS` but `asynchronously to different region`

- Geo-zone-redundant storage (GZRS) = `6 copies` = `3 copies` across separate AZs within the primary region (ZRS) + `3 copies` within the secondary region (LRS)
  - ** copies your data `synchronously` across `three Azure availability zones` in `the primary region`. 
    - >> Primary region duplication = `ZRS`.
  - ** It then copies your data `asynchronously` to `a single physical location` in `the secondary region`.
    - >> Secondary region duplication ~ `LRS` but `asynchronously to different region`




Azure Content Delivery Network ~ CloudFront
- Content Delivery Network is a distributed network of servers that can efficiently deliver web content to users. CDNs store cached content on edge servers in point-of-presence (POP) locations that are close to end-users to minimize latency.





Azure Application Gateway ~ ALB
- is a web traffic load balancer that enables you to manage traffic to your web applications.

- Application Gateway can make routing decisions based on `additional attributes of an HTTP request`, for example, `URI path` or `host headers`. For example, 
  - you can route traffic based on the `incoming URL`. So if /images are in the incoming URL, you can route traffic to a specific set of servers (known as a pool) configured for images. If /video is in the URL, that traffic is routed to another pool that’s optimized for videos.

- Azure Application Gateway can be used as `an internal application load balancer` or as `an internet-facing application load balancer`.

  - An `internet-facing application gateway` uses `public IP addresses`. 
    - The DNS name of an internet-facing application gateway is publicly resolvable to its public IP address. 
    - As a result, internet-facing application gateways can route client requests to the internet.

  - `Internal application gateways` use only `private IP addresses`. 
    - If you are using a `Custom or Private DNS zone`, the domain name should be internally resolvable to the `private IP address` of `the Application Gateway`. 
    - Therefore, internal load-balancers can only route requests from clients with access to a virtual network for the application gateway.




Azure App Service
- this service just enables you to build and host web apps, mobile back ends, and RESTful APIs in the programming language of your choice without managing infrastructure.




Azure Monitor ~ CloudWatch
- helps you maximize the availability and performance of your applications and services. 
- It delivers a comprehensive solution for collecting, analyzing, and acting on telemetry from your cloud and on-premises environments. 
- This information helps you understand how your applications are performing and proactively identify issues that affect them and the resources they depend on.




Application Insights
- is `a feature` of `Azure Monitor`
- an extensible `Application Performance Management (APM)` service for developers and DevOps professionals. 
- You can use this to `monitor your live applications` to `automatically detect performance anomalies`



Azure AD Connect
- this service is primarily used to provide `robust monitoring` of `your on-premises identity infrastructure`.




Azure Storage Account :: Blob storage versioning

- You can enable `Blob storage versioning` to automatically maintain previous versions of an object. 
  - ** When blob versioning is enabled, you `can restore` an earlier version of a blob to recover your data if it is erroneously `modified` or `deleted`.
    - ** You can `recover deleted data` within Azure storage accounts that have versioning enabled.

- `Blob versioning` is enabled on the storage account and applies to `all blobs in the storage account`. After you enable blob versioning for a storage account, Azure Storage automatically maintains versions for `every blob in the storage account`.




Q: What are the types of locks in Azure that protect you from accidentally deleting an Azure resource?
A:
- Management Locks – CanNotDelete
- Management Locks – Read-only

Reason:
- As an administrator, you may need to lock `a subscription`, `resource group`, or `resource` to prevent other users in your organization from `accidentally deleting or modifying critical resources`. You can set the `lock level` to `CanNotDelete` or `ReadOnly`:

  - `CanNotDelete` means authorized users `can still read and modify a resource`, but they `can’t delete the resource`.

  - `ReadOnly` means authorized users `can read a resource`, but they `can’t delete or update the resource`. 
    - Applying this lock is similar to `restricting all authorized users` to the permissions granted by the `Reader` role.




NOTE: Azure Active Directory – Conditional Access
- this is merely a tool used by Azure Active Directory to bring signals together, make decisions, and enforce organizational policies.



NOTE: Azure Active Directory – smart lockout 
- this is primarily used to lockout intruders that try to guess your users’ passwords or use brute-force methods in Azure Active Directory.



NOTE: SMB File Locking
- this is only a file system locking mechanism in Azure File service that is used to manage access to a shared file.




WRONG: "Two virtual machines that use D2d v4 instance will `always be billed the same monthly costs`"
- This statement is INCORRECT because despite having `the same instance type`, they may differ on the following specifications: type of OS, region location of each virtual machine, and storage size, type, and transaction. These must always be specified when creating a virtual machine.




NOTE: `Capital expenditures` generate `benefits over a long period`. These expenditures are generally `nonrecurring` and result in `the acquisition of permanent assets`.



NOTE: `Operating expenditures` are `ongoing costs of doing business`. Consuming cloud services in `a pay-as-you-go model` could qualify as an operating expenditure




Azure Arc
- used to consistently manage `multi-cloud` and `on-premises` environments using ONLY the `Azure portal`.
- simplifies governance and management by delivering a consistent `multi-cloud` and `on-premises` management platform.
- Azure Arc provides a centralized, unified way to:

  - Manage your entire environment together by projecting your existing non-Azure and/or on-premises resources into `Azure Resource Manager`.

  - Manage virtual machines, Kubernetes clusters, and databases as if they are running in Azure.

  - Use familiar Azure services and management capabilities, regardless of where they live.

  - Continue using traditional ITOps while introducing DevOps practices to support new cloud-native patterns in your environment.

  - Configure custom locations as an abstraction layer on top of Azure Arc




Azure Migrate
- this service provides a simplified migration, modernization, and optimization service for Azure.



Azure Site Recovery
- this simply helps ensure business continuity by keeping business apps and workloads running during outages by replicating workloads running on physical and virtual machines (VMs) from a primary site to a secondary location. This service is mainly used for disaster recovery plans.




Azure Sphere
-  this is just a secure, high-level `application platform` with `built-in communication and security features` for `Internet-connected devices`.




Azure CycleCloud
- this is primarily designed to enable enterprise IT organizations to provide `secure and flexible` `cloud HPC` and `Big Compute environments` to their end-users.
- With `the dynamic scaling of clusters`, the business can get the resources it needs at the right time and the right price.




Microsoft Defender for Cloud
- this service is just `a unified infrastructure security management system` that strengthens the security posture of `your data centers` and provides `advanced threat protection` across `your hybrid workloads in the cloud`.

- Microsoft Defender for Cloud provides you `the tools needed to harden` your network, secure your services and make sure you’re on top of your security posture. With Microsoft Defender for Cloud, you can do the following:
  - Evaluate your regulatory compliance using the Regulatory compliance dashboard.
  - Improve your compliance posture by taking action on recommendations.

- ** NOTE: It is NOT designed for `security orchestration and automated response (SOAR)` or to be a `SIEM` tool.

- NOTE: This service also allows you to use `just-in-time (JIT) VM access` when you need it.
  - `Lockdown inbound traffic to your Azure Virtual Machines` with Microsoft Defender for Cloud’s just-in-time (JIT) virtual machine (VM) access feature. 
  - This `reduces exposure to attacks` while `providing easy access when you need to connect to a VM`.





Microsoft Sentinel

- Microsoft Sentinel is a scalable, cloud-native, `security information event management (SIEM)` and `security orchestration automated response (SOAR)` solution.

- provides you with `a birds-eye view` across the enterprise.

- provides a proactive and responsive `cloud-native SIEM` that will help customers simplify their security operations and scale as they grow.

- Microsoft Sentinel delivers `intelligent security analytics` and `threat intelligence` across the `enterprise`, providing a single solution for `alert detection`, `threat visibility`, `proactive hunting`, and `threat response`.

- Microsoft Sentinel is your birds-eye view across the `enterprise` alleviating the stress of increasingly sophisticated attacks, increasing volumes of alerts, and long resolution timeframes.

  - Collect data at cloud scale across all users, devices, applications, and infrastructure, both on-premises and in multiple clouds.

  - Detect previously undetected threats, and minimize false positives using Microsoft’s analytics and unparalleled threat intelligence.

  - Investigate threats with artificial intelligence, and hunt for suspicious activities at scale, tapping into years of cybersecurity work at Microsoft.

  - Respond to incidents rapidly with built-in orchestration and automation of common tasks.





Azure Information Center
- is just `a cloud-based solution` that enables organizations to discover, classify, and protect `documents` and `emails` by `applying labels to content`.




Q: Your company is planning to migrate its TDPortalApp to Azure. You need a solution that will `maintain virtual machine connectivity` to `at least one instance` with `a 99.95% uptime`.
A: Deploy `two or more VM instances` in `the same Availability Set`.

Reason:
- `An Availability Set` is `a logical grouping of VMs` within a data center that is `automatically distributed across these fault domains`. 
  - There is no cost for the Availability Set itself, you only pay for each VM instance that you create.
  - `By default`, the virtual machines configured `within your availability set` are separated across `up to three fault domains` for Resource Manager deployments.

- `Fault domains` define `the group of virtual machines` that `share a common power source and network switch`. >> Die together

- ** For all Virtual Machines that have `two or more instances` deployed in `the same Availability Set`, Azure guarantees that you will `have Virtual Machine Connectivity` to `at least one instance` `at least 99.95% of the time`.





Azure Service Health
- provides you with a customizable dashboard that tracks the health of your `Azure services` `in the regions where you use them`.
- The `Service Health dashboard` helps you track active events like ongoing service issues, upcoming planned maintenance, or relevant health advisories.
- When events become inactive, they get placed in `your health history for up to 90 days`.
- You can also use the dashboard to create and manage `service health alerts` that proactively notify you when service issues are affecting you.

Azure Service Health is a combination of `three separate smaller services`:

- `Azure status`
  - informs you of `service outages in Azure` on the `Azure Status page`.
  - ** The page is `a global view of the health` of `all Azure services` across `all Azure regions`. 
  - The status page is a good reference for incidents with widespread impact, but Azure strongly recommends that the current Azure users leverage Azure `service health` to `stay informed about Azure incidents and maintenance`.

- `Service health` (<> `Azure status`)
  - ** provides `a personalized view` of the health of the Azure services and regions `you’re using`.
  - This is the best place to look for service-impacting communications about outages, planned maintenance activities, and other health advisories because the authenticated Service Health experience `knows which services and resources you currently use`. 
  - ** The best way to use `Service Health` is to set up `Service Health alerts` to notify you via your preferred communication channels when service issues, planned maintenance, or other changes may affect the Azure services and regions you use.

- `Resource health` 
  - ** provides information about the health of `your individual cloud resources`, such as a specific virtual machine instance. 
  - ** Using `Azure Monitor`, you can also configure `alerts` to notify you of availability changes to your cloud resources. 
  - `Resource Health`, along with `Azure Monitor notifications`, will help you stay better informed about the availability of your resources minute by minute and quickly assess whether an issue is due to a problem on your side or related to an Azure platform event.



NOTE: Load Balancer Services
- `Azure Front Door` = `Global` load balancing and `site acceleration` service
- `Traffic Manager` = A `DNS-based traffic` load balancer
- `Application Gateway` = `Layer 7` `regional` load balancer
- `Azure Load Balancer` = `Layer 4` `regional` load balancer




Azure Front Door

- enables you to define, manage, and monitor `the global routing` for your web traffic by optimizing for best performance and quick global failover for high availability.

- It works at `Layer 7` or `HTTP/HTTPS layer` and uses `anycast protocol with split TCP` and Microsoft’s global network for improving global connectivity. 

- So, per your routing method selection in the configuration, you can ensure that Front Door `is routing your client requests` to `the fastest and most available` application backend.






Azure Traffic Manager

- is `a DNS-based traffic` load balancer that enables you to distribute traffic optimally to services across `global Azure regions` while providing high availability and responsiveness.

- Traffic Manager `uses DNS to direct client requests` to `the most appropriate service endpoint` based on `a traffic-routing method` and `the health of the endpoints`. 

- An endpoint is `any Internet-facing service` hosted `inside or outside of Azure`. 

- Traffic Manager is `resilient to failure`, including `the failure of an entire Azure region`.




Application Gateway 

- is `a web traffic load balancer` that enables you to manage traffic to your web applications using various `Layer 7` load-balancing capabilities. 
  - Traditional load balancers operate at the transport layer (OSI layer 4 – TCP and UDP) and route traffic based on source IP address and port, to a destination IP address and port. 

- It supports `TLS termination` at the gateway, after which traffic typically flows unencrypted to the backend servers.




Azure Load Balancer 
- operates at `layer four` of the Open Systems Interconnection (OSI) model. 

- It’s `the single point of contact for clients`. 

- Load Balancer distributes inbound flows that arrive at the load balancer’s front end to `backend pool instances`. 

- These flows are according to configured load balancing rules and health probes. 

- The backend pool instances can be Azure Virtual Machines or instances in a virtual machine scale set.



NOTE: Azure Virtual Network, route tables, and network security groups are free of charge.

NOTE: ** All `Instance level public IP addresses (ILPIP)` are charged for a certain amount.
- Public IP prefixes are charged per IP per hour. As soon as a prefix is created, you are charged.




NOTE: When you store data in an `Archive` access tier, the data 
`must be rehydrated first before you can access the data`.

- ** While a blob is in the `archive` access tier, it’s considered `offline` and `can’t be read or modified`. 
  - The blob metadata remains online and available, allowing you to list the blob and its properties.
  - Reading and modifying blob data is only available with online tiers such as `hot or cool`.

- ** To read data in archive storage, you must `first change the tier of the blob to hot or cool`. This process is known as `rehydration` and can take `hours to complete`.

- It is recommended to use `large blob sizes` for optimal `rehydration` performance. 
  - `Rehydrating` `several small blobs` concurrently may add `additional time`.

- There are currently `two rehydrate priorities`, `High` and `Standard`, which can be set via the optional x-ms-rehydrate-priority property on a `Set Blob Tier` or `Copy Blob` operation.
  - Meaning that you can `copy` over data from the `archive access tier` to `hot access tier`.
  - You can do this by utilizing the `Copy Blob` operation and archive blobs can `ONLY` be copied to online destination tiers `within the same storage account`.

NOTE: The archive access tier data must remain in the archive tier for `at least 180 days` 
- ** OR be subject to an early deletion charge.
  - Meaning that you can delete still your data in the archive access tier `EVEN during the first day`. 
  - However, Deleting or rehydrating archived blobs `before 180 days` will incur `early deletion fees`.




Q: What are two possible solutions to ensure `segmentation between departments` in a company?
A: 
- Deploy multiple `subscriptions`
- Deploy multiple `resource groups`




NOTE: Remember these two important concepts about resource groups:
- When you delete a resource group, all resources in the resource group are also deleted.
- Azure resource groups are regional in scope but it can contain Azure resources that span to multiple regions.

** Generally, you can assign `role-based access controls` for your `users/teams/departments` to your `subscription`. The permissions assigned will trickle down to the `resource groups` and `resources` under that `subscription`.



---
