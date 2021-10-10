# Microsof-Azure
A Repository with some descriptions about Azure (Resources, Services)

#### Shadi Badir - Microsoft Azure

## Documentaion:

### SSH key more secure than password ?
The first pro is that SSH keys are more difficult to hack than passwords and thus are more secure. SSH keys can be up to 4096 bits in length, making them long, complex, and difficult to brute-force hack. ... And unlike passwords, your private SSH key isn't sent to the server.

---

### Why I've choosed VM size (B2ls) ?
The B-Series offers a cost effective way to deploy these workloads that do not need the full performance of the CPU continuously and burst in their performance. While B-Series VMs are running in the low-points and not fully utilizing the baseline performance of the CPU, your VM instance builds up credits. When the VM has accumulated enough credit, you can burst your usage, up to 100% of the vCPU for the period of time when your application requires the higher CPU performance.

---

### Availability Zone

- 1. This features help provides better availability for your application by protecting them from datacenter failures.

- 2. Each Availability zone is a unique physical location in an Azure region.

- 3. Each zone comprises of one or more data centers that has independent power, cooling, and networking

- 4. Hence the physical separation of the Availability Zones helps protect applications against data center failures

- 5. Using Availability Zones, you can be guaranteed an availability of 99.99% for your virtual machines. You need to ensure that you have 2 or more virtual machines running across multiple availability zones

An interesting fact - Does it cost more to use an Availability Zone. Well no, you don't get charged separately for the use of Availability Zones.

---


### Availability Sets
When you host your virtual machines in Azure, you sometimes need to cater to the following

- An unplanned event wherein the underlying infrastructure fails unexpectedly. The failures could be attributed to network failures , local disk failures or even rack failures.

- Planned maintenance events , wherein Microsoft needs to make planned updates to the underlying physical environment. In such cases , a reboot might be required on your virtual machine.

You can increase the availability of your application by making use of availability sets. Each virtual machine that is assigned to the availability set is assigned a separate fault and update domain.

**Fault domains** : are used to define the group of virtual machines that share a common source and network switch. You can have up to 3 fault domains.

**Update domains** : are used to group virtual machines and physical hardware that can be rebooted at the same time. You can have up to 20 update domains.

If you deploy two or more virtual machines in an Availability set, you will get a guarantee of virtual machine connectivity to at least one virtual machine 99.95% of the time.

---

### Azure Virtual Network

The Azure Virtual Network service is used to define an isolated network in Azure. The virtual network can then be used to host your resources such as Azure virtual machines.

The Azure virtual network gets assigned an address space which you specify when you create an Azure virtual network

You can then add subnets to your Azure virtual network. This helps divide your network into more logical segments.

An example is shown below of having multiple subnets. You could have one subnet named SubnetA in the virtual network to host your Web servers and another subnet to host the Database servers.

When you create a virtual machine in a virtual network, the virtual machine gets a Private IP address from the address space of the subnet is it launched in.

--- 

### Network Security Groups

These are used to filter network traffic to and from Azure resources in an Azure virtual network.

A network security group is attached to the network interface attached to the virtual machine.

- A network security group consists of Inbound rules that are used to control the traffic inbound into a virtual machine

- By default all traffic into a virtual machine is DENIED.

- You have explicitly add rules to allow traffic into a virtual machine

- There are also outbound rules to control the traffic flowing out of the virtual machine. By default all traffic outbound onto the Internet is allowed.

---

### Virtual Network Peering

- Virtual Network Peering is used to connect two Azure virtual networks together via the backbone network.

- Azure supports connecting two virtual networks located in the same region or networks located across regions.

- Once you enable virtual network peering between two virtual networks, the virtual machines can then communicate via their private IP addresses across the peering connection.

- You can also peer virtual networks that are located across different subscriptions.

- The virtual networks can't have overlapping CIDR blocks.

---

### Point-to-Site VPN Connection

A Point-to-Site VPN connection is used to establish a secure connection between multiple client machines and an Azure virtual network via the Internet.

Image reference -https://docs.microsoft.com/en-us/azure/vpn-gateway/vpn-gateway-howto-point-to-site-resource-manager-portal

To implement a Point to Site VPN connection, you need to create a VPN Gateway in Azure.

---

### Site-to-Site VPN Connection

A Site-to-Site VPN connection is used to establish a secure connection between an on-premise network and an Azure network via the Internet.

Image reference - https://docs.microsoft.com/en-us/azure/vpn-gateway/vpn-gateway-howto-site-to-site-resource-manager-portal

- On the on-premise side, you need to have a VPN device that can route traffic via the Internet onto the VPN gateway in Azure. The VPN device can be a hardware device like a Cisco router or a software device ( e.g Windows Server 2016 running Routing and Remote services). The VPN device needs to have a publically routable IP address.

- The subnets in your on-premise network must not overlap with the subnets in your Azure virtual network

- The Site-to-Site VPN connection uses an IPSec tunnel to encrypt the traffic.

- The VPN gateway resource you create in Azure is used to route encrypted traffic between your on-premise data center and your Azure virtual network.


---

### High Availability

This refers to technologies that can be used to minimize IT disruptions by ensuring applications and infrastructure is made fault-tolerant.
Let's say that you had the following architecture for your application. Your application is hosted on a single virtual machine.

What happens if the virtual machine goes down for any reason, your application would not be available.

To make your application more redundant and more tolerant to failures, why not host your application on a collection of servers

Even if one machine were to go down , you would still have the other one available. This makes your application more tolerant to infrastructure level failures.

You can also increase the availability for your virtual machines by distributing them across Availability Zones or Availability Sets.

---

### Disaster Recovery

This refers to the concept of minimizing IT disruptions by recovering them to another data center that could be located hundreds to miles away from the original data center hosting your application.

Your application is running on virtual machines in the West US region. Here the users are accessing your application.

At the same time, you might have the application hosted in another region (East US). The application might be in a shutdown state. This is only meant to be running if the primary region goes down for any reason.

Not lets say there is a disaster in the West US region and all the data centers go down.

To minimize any disruption to your users , the requests to the application could now be redirected to the application in the East US region. So now you would start the application here and make sure all requests are routed to the secondary region.


---

### Elasticity

Elasticity refers to the concept of how flexible your architecture can scale based on demand.
For virtual machines , you can increase or decrease the size of the virtual machine at any point in time.

---

## Cloud Service Model
#### The different cloud service models

### Infrastructure as a service (IaaS)

- An example is the Azure virtual machine service.

- Here you don’t need to manage the underlying infrastructure.

- The physical servers and storage is managed for you.

- This helps remove the capital expense and reduces ongoing cost.

- The Virtual Machine also has an SLA. To achieve that SLA for any on-premise server would require a lot of work.

- Infrastructure cloud services also allow you to scale based on demand.



### Platform as a service

- An example is the Azure SQL Database service or the Azure Web App service.

- Here you don’t need to manage the infrastructure or even the underlying operating system and platform components.

- You can just start hosting your data or your web application.

- Reduces development time.

- You can use an array of database technologies available in the case of Azure.

- All of these services use a Pay-as-you-go model.



### Software as a service

- An example is Microsoft Office 365.

- Here you don’t need to manage the infrastructure or even the underlying operating system, platform components or even the software.

- Here you just start directly using the software.

- You can access your application data from anywhere.

- You don’t have the headache of managing anything.

---

## Cloud Models
### Public Cloud

- These are services that are offered over the public internet.

- It’s available to anybody who wants to use them. Users then pay based on service they use.

- Here all the servers and storage is managed by the cloud provider

---

### Advantages of the Public Cloud

- No need for a capital investment – You normally don’t pay any money upfront to use a cloud service. Most of the services are based on a pay-as-you-go model.

- You don’t need to manage the underlying physical infrastructure. Hence on-going maintenance costs are also reduced.

- Cloud providers such as Azure have data centers located at different regions across the world.

- You can quickly provision resources on the cloud. It allows you to get up and running in no time.

---

### Private Cloud

- These are set of services that are normally only used by users of a business or organization.

- The private cloud could be hosted either on the company’s on-premise environment. Or it could be provided by a third-party service provider.


---

### Advantages of the Private Cloud

- The business has complete control over the environment.

- They can implement their own security protocols at every layer to secure the environment.

- The data held in the environment is in complete control by the business.

---

### Hybrid Cloud

- This is a combination of both the public and private cloud.

- It allows data and applications to be shared across both cloud environments.

---

### Advantages of the Hybrid Cloud

- Businesses can still leverage their existing on-premise environment. This is important if they have already made a substantial investment in getting their environment in place.

- They can keep data which needs to be secured by their standards in their on-premise environment.

- They can extend their infrastructure to the cloud without making a further investment.

 They can move workloads to the cloud gradually.


---

### Azure App Service

- This is an HTTP-based service that allows you to host web applications, REST API's and mobile back ends. You can develop a program in programming languages such as .NET, .NET Core, Java, Ruby, Node.js, PHP and Python.

- Here you don't need to manage the underlying infrastructure. It allows you to focus on code development.

- Each App service needs to be associated with an App Service Plan.

- Each App service plan has an associated cost per month and also has specific features based on the plan you choose.

---

### Virtual Machine Scale Sets

- This service allows you to create and manage a group of identical load balanced virtual machines.

- Here the number of Virtual Machine instances in the scale set can scale based on demand

- This is the best service if you want to add scalability to your application

---

### Azure Load Balancer

- The Azure Load balancer is used to distribute incoming network traffic to a backend group of servers.

- This service helps increase the availability of your entire application architecture

the Load Balancer would take the incoming requests from the users and direct the requests to virtual machines running in an Azure virtual network.

If you have a web application running on the backend virtual machines, the requests would be distributed across the virtual machines by the Azure Load Balancer.

#### Other tools to access Azure resources
You can use other tools to access and work with Azure resources

- You can use PowerShell which can work on Windows, macOS and Linux

- You can use the Azure command line interface which can work on Windows, macOS and Linux

- You can use Azure cloud shell from the browser, which can then work on any operating system which has browser support

---

### Azure Functions

- This service allows you to run small pieces of code as functions.

- Here you just develop and upload the code to an Azure Function.

- You only get billed for the amount of time the code is run.

- You can use a variety of programming languages in Azure Functions.

- C#, Java , JavaScript, PowerShell and Python.

- You can use libraries by using NuGet and NPM packages.



#### Pricing plans available for Azure Functions

**Consumption Plan** – Here you only pay for the time the code runs.

**App Service Plan** – If you already have an App Service plan that runs a web application, you can reuse the same plan to run Azure Functions. This would save on cost if you already have an App Service Plan in place.

**Premium Plan** – Here you get a number of pre-warmed instances that are always online and ready to run your functions. The plan also automatically adds more compute when required.

You can also invoke your functions via various triggers

---

### Azure Logic Apps

This is a cloud service that helps you schedule, automate and orchestrate tasks , business processes and workflows.

#### How it works

- You first design a workflow in Azure Logic Apps

- Each workflow starts with a trigger.

- The trigger is fired via a specific event

- When the trigger is fired , the Logic App engine creates a logic app instance that runs the workflow.



#### Connectors for Azure Logic Apps

- These connectors provide easy access to event, data and actions that are sent from external applications, services , systems or platforms.

- You have built-in connectors that can connect to Azure services such as Azure functions, Azure API Apps etc.

- You have Managed connectors that can connect to platforms such as Office 365, Microsoft Dynamics.

--- 

### Azure Traffic Manager

The Azure Traffic Manager service is a DNS-based traffic load balancer that distributes traffic across services that are distributed across different Azure regions.

The Traffic Manager service is used to direct client requests to the most appropriate service endpoint that is based on a traffic-routing method and the health of the endpoints.

The different traffic routing methods available for the Azure Traffic Manager are

- Priority – Route traffic to another endpoint in case the primary fails.

- Weighted – Route traffic to different endpoints based on weight.

- Performance - you want end users to use the "closest" endpoint in terms of the lowest network latency.

- Geographic - geographic location their DNS query originates from.

- Multivalue – Here different endpoints are sent to the client. The client then selects the endpoint to send the request to.

- Subnet – This maps a set of end-user IP address ranges to a specific endpoint within a Traffic Manager profile.

---

### Azure Kuberntes
#### What is Kubernetes?

- This is an open-source platform that is used to managing containerized workloads.

- Kubernetes is able to provide a DNS name to your container.

- If there is a high load on your containers , Kubernetes can load balance and distribute network traffic.

- Kubernetes can also restart containers that fail.

- It can be used to replace or kill containers.

- It also helps to store and manage sensitive information such as passwords, OAuth tokens and ssh keys



#### What is Azure Kubernetes?

Fully managed Kubernetes service on Azure.

Makes it easy to deploy and manage containerized applications.

It helps to remove the burden of managing the underlying infrastructure for the Kubernetes deployment.

---

### Azure Content Delivery Network

This is an ideal service to use for your web applications. If you need content to be distributed to users across the world for your web sites , then its ideal to use the Azure Content Delivery Network Service

- Here the users are directed on various Edge servers by the Content Delivery Network service.

- The Edge servers will get the content from your web site and also cache frequently accessed content.

- The Edge servers are located across the world , so it gives all users a seamless experience when it comes to accessing your web site

---

