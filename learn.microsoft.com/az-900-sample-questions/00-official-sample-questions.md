# Official sample questions

## Reference: 
- https://learn.microsoft.com/en-us/certifications/resources/az-900-sample-questions?azure-portal=true#questions

Q: Which Azure Active Directory (Azure AD) feature is used to provide access to resources based on organizational policies?
A: Conditional Access
- Conditional Access is the tool used by Azure Active Directory to allow (or deny) access to resources based on `identity signals`. 
- Conditional access is`a more refined MFA (multifactor authentication) method`.

Q: Which option is used to set the communication between an on-premises VPN device and an Azure VPN gateway through an encrypted tunnel over the internet?
A: Site-to-Site VPN

Q: Which defense in depth layer uses distributed denial of service (DDoS) protection?
A: Perimeter layer



`Azure Logic Apps` are designed in `a web-based designer` and can execute logic triggered by Azure services `without writing any code`.
- NOT `Azure Functions` that we need to write some codes.



`Azure Batch` allows you to `scale to thousands of virtual machines` for `high-performance computing (HPC)` and `large-scale parallel jobs`. 
- Other Azure functionalities allow you to `scale multiple VMs`, but only Azure Batch will allow for `thousands of VMs` for HPC.



`An Azure virtual machine scale set` enables you to provision a group of matching and load-balanced virtual machines in Azure.
- NOTE: It just do both auto-scaling and load-balancing for you.



What is the difference between `scale set` and `availability set` in Azure?
- Scale set is a collection of instances sizes
  - You can use scale set to configure the number of instances that a given application can run on
- Availability set is a collection of availability zones.
  - You can use availability set to configure the number of zones in which your application can run.



A Point-to-point Ethernet connection is supported by `ExpressRoute` for connecting your `on-premises network` to `Azure`.
- The three models that ExpressRoute supports are:
  - CloudExchange colocation
  - * Point-to-point Ethernet connection
  - Any-to-any-connection

---
