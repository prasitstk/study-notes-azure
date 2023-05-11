# Review mode

NOTE: `Azure virtual machines` are `billed by the second` and not per hour.

NOTE: `Any disks` that are attached to an Azure virtual machine will actually `not be deleted if its VM is deleted`. 
- This underlying mechanism helps to prevent data loss due to the unintentional deletion of VMs.
- after a VM is deleted, you will still `continue to pay for unattached disks`.

NOTE: `Disks` attached to `stopped virtual machines` do `still incur costs`



Azure Hybrid Benefit
- Maximizes the value of your existing on-premises Windows Server and/or SQL Server license in Azure.
- Azure Hybrid Benefit for Windows Server allows you to use your `on-premises Windows Server licenses` and run Windows `virtual machines on Azure` at a `reduced cost`. You only pay for the compute costs of a Windows virtual machine.



IMPORTANT: `A reserved capacity` is different from `a reserved instance`.

- `A reserved capacity` is mainly used for `Azure database services` such as Azure SQL Database, Azure Cosmos DB, Azure Synapse Analytics, and Azure Cache for Redis.

- By purchasing `a reserved instance`, you can significantly reduce costs up to 72 percent compared to pay-as-you-go pricing. A reserved instance has `a one-year or three-year` term on Windows and Linux `virtual machines`. You can pay for a reservation upfront or monthly.



`Federation` 
- this is primarily the process of granting users single sign-on (SSO) access to an external system. 
- If a user connection is terminated or if the user leaves, the account can immediately be disabled and its access revoked.



NOTE: Azure resource groups are `regional` in scope but `can contain Azure resources that span to multiple regions` = `Resources` in `a resource group` CAN be located in `different regions` than the resource group. >> The statement `Resource groups CAN span multiple regions` should be right.
- `A resource group` stores `metadata about the resources`. 
- When you specify `a location for the resource group`, you’re specifying `where that metadata is stored`.

NOTE: `Resources` CAN `connect` to other resources located in `another resource group`.

NOTE: If you `delete a resource group`, The `resources` inside it will be `deleted`.

NOTE: A resource group’s permission will be inherited by the resources inside it.

NOTE: ** When you assign a tag to a resource group, the resources within that group will NOT inherit the tag.





Azure role-based access control (Azure RBAC)
- Azure RBAC has several `Azure built-in roles` that you can assign to `users, groups, service principals, and managed identities`:

  - The `Owner` role lets you manage everything, including access to resources and the contributor’s role. It grants you full access to `manage all resources`, including `the ability to assign roles` in Azure RBAC.

  - The `Contributor` role grants you full access to `manage all resources` but does `not allow you to assign roles` in Azure RBAC.

  - The `Reader` role lets you `view everything`, but `not make any changes`.

  - `Virtual Machine Contributor` role lets you `manage virtual machines`, but `not access to them`, and `not the virtual network or storage account` they’re connected to.

  

Azure virtual machine `scale sets`
- let you create and manage `a group of load-balanced VMs`. 
- The number of VM instances can `automatically increase or decrease` in response to demand or a defined schedule. 
- Scale sets provide the following key benefits:
  - `Easy` to create and manage multiple VMs
  - ** Provides `high availability` and application resiliency by distributing VMs `across availability zones` or fault domains >> NOT just Availability Sets
  - Allows your application to `automatically scale` as resource demand changes



Azure `availability set`
- this feature simply is a logical grouping capability that ensures the VMs you place within an Availability Set `run across multiple physical servers, compute racks, storage units, and network switches`. 
- If a hardware or software failure happens, only a subset of your VMs are impacted and your overall solution stays operational.






Microsoft Defender for Cloud
- is a tool for `security posture management` and `threat protection`.

- Defender for Cloud collects, analyzes, and integrates `log data` from your `Azure resources`, the network, and connected partner solutions, such as firewalls and endpoint agents. 
  - Defender for Cloud uses the `log data` to detect `real threats` and reduce `false positives`. 
  - A list of prioritized security alerts is shown in Defender for Cloud, along with the information you need to quickly investigate the problem and steps to take to remediate an attack.

- ** With its integrated `Microsoft Defender plans`, `Defender for Cloud` protects workloads running in `Azure, on-premises, and multicloud` (Amazon AWS and Google GCP) resources.

- NOTE: Microsoft Defender for Cloud `advanced security management features` are `NOT enabled by default`.

- NOTE: Microsoft Defender for Cloud  allows you to use `just-in-time (JIT) VM access`.
  - Lockdown inbound traffic to your Azure Virtual Machines with Microsoft Defender for Cloud’s just-in-time (JIT) virtual machine (VM) access feature. 
  - This reduces exposure to attacks while providing easy access when you need to connect to a VM.




Platform as a Service (PaaS) solutions
- Azure App Service
- Azure SQL Databases
- Azure Storage accounts




`Azure Active Directory – smart lockout` is primarily used to `lockout intruders` that try to `guess your users’ passwords or use brute-force methods` in `Azure Active Directory`.



`Azure Active Directory – Conditional Access` is merely a tool used by `Azure Active Directory` to `bring signals together`, make decisions, and `enforce organizational policies`.






While a blob is in the `archive access tier`, it’s considered `offline` and `can’t be read or modified`. 
- The blob metadata remains online and available, allowing you to list the blob and its properties. 
- `Reading and modifying` blob data is only available with `online tiers` such as `hot or cool`.

** To read data in archive storage, you must `first change the tier of the blob to hot or cool`. 
- This process is known as `rehydration` and can `take hours` to complete.

It is recommended to use `large blob sizes` for optimal rehydration performance. Rehydrating several small blobs concurrently may add additional time.

There are currently `two rehydrate priorities`, `High and Standard`, which can be set via the optional x-ms-rehydrate-priority property on a `Set Blob Tier` or `Copy Blob` operation.

NOTE:
- ** you can delete your data on archive access tier even during the first day. Deleting or rehydrating archived blobs `before 180 days` will `incur early deletion fees`.
- you can copy over data from the archive access tier to hot access tier. 
  - You can do this by utilizing the `Copy Blob` operation and archive blobs can only be copied to online destination tiers `within the same storage account`.




Azure Active Directory Identity Protection
- Ex. automatically prompt a user to change the password if the user `signs in from an anonymous IP address`.

Identity Protection is a tool that allows organizations to accomplish three key tasks:
– Automate the detection and remediation of identity-based risks.
– Investigate risks using data in the portal.
– Export risk detection data to third-party utilities for further analysis.




Microsoft Defender for Identity is only a cloud-based security solution that `leverages your on-premises Active Directory signals` to identify, detect, and investigate advanced threats, compromised identities, and malicious insider actions directed `at your organization`. 




Azure AD Privileged Identity Management is incorrect because this just provides `a time-based and approval-based role activation` to mitigate the risks of excessive, unnecessary, or misused access permissions on resources that you care about.





The data moving in and out of Azure data centers, as well as data moving between Azure datacenters, is called `bandwidth`.

Remember these concepts regarding data transfer:

- ** Data transfer `to Azure` is `always free`

- ** Data transfer `between Availability Zones` is `not free`

- ** Data transfer `within the same Availability Zone` is `free`

- ** Data transfer `between Azure regions` and to other continents is `not free`




Azure Cost Management + Billing ALSO provides recommendations on how you can optimize and improve the efficiency of your workloads by `identifying idle and underutilized resources`.



NOTE: `Network Security Groups` can be attached to `subnets` and/or `network interfaces`.
- NOT others like Virtual Network, Route Table, and DNS Server 






`Azure Advisor` only provides a list of Azure VMs that are `NOT properly backed up` and not the other way around.

`Azure Advisor` can only provide `limited security recommendations` for `Azure Active Directory`. 
- It is not capable of calculating `user risk levels` or providing `custom Active Directory recommendations`. 
- ** These functions can only be provided by `Azure AD Identity Protection`.

NOTE: Your `secure score` in `Microsoft Defender for Cloud` will increase if you remediate all of the security recommendations provided by `Azure Advisor`.





Azure virtual network TAP (Terminal Access Point)
- this just allows you to continuously stream your virtual machine network traffic to a network packet collector or analytics tool.




Azure Firewall is a managed, cloud-based network security service that protects your Azure Virtual Network resources. It’s a fully stateful firewall as a service with built-in high availability and unrestricted cloud scalability.
- Compared with network security group:
  
  - Network security groups provide distributed network layer traffic filtering to limit traffic to `resources within virtual networks in each subscription`.
  
  - Azure Firewall is a fully stateful, centralized network firewall as-a-service, which provides network- and application-level protection across `different subscriptions and virtual networks`.




NOTE: Sync the on-premises Active Directory to Azure Active Directory using AD connect.
- Azure `AD Connect` installs an on-premises service that orchestrates synchronization between your on-premises Active Directory and Azure Active Directory. 
- The Microsoft `Azure AD Sync` synchronization service (ADSync) runs on a server in your on-premises environment.




Use `Azure AD Connect Health` to monitor your on-premises identity infrastructure and ensure a reliable connection to Office 365 and Microsoft Online Services.




You need to create or have `a subscription` first to create resources on `Azure`. 

`A subscription` is an agreement with Microsoft to use one or more Microsoft cloud platforms or services, for which charges accrue based on either `a per-user license fee` or on `cloud-based resource consumption`.

- Microsoft’s `Software as a Service (SaaS)-based` cloud offerings (`Microsoft 365` and `Dynamics 365`) charge `per-user license fees`.

- Microsoft’s `Platform as a Service (PaaS)` and `Infrastructure as a Service (IaaS)` cloud offerings (Azure) charge based on `cloud resource consumption`.




Microsoft Defender for Cloud
- enables you to evaluate the `regulatory compliance` as well as improve `the compliance posture` of your Azure environment
- ** NOT Azure Blueprints
  - It defines a repeatable set of Azure resources that implement and adhere to your organization’s standards, patterns, and requirements and rapidly build new environments with a set of built-in components to speed up development and delivery.




---
