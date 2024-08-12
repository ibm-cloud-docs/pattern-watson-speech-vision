---
copyright:
  years: 2024
lastupdated: "2024-03-14"

subcollection: pattern-watson-speech-vision

keywords:
---
{{site.data.keyword.attribute-definition-list}}

# Network design

{: #networking-design}

For deploying AI applications, it's essential to design a robust and scalable network infrastructure that can handle the unique demands of these workloads. THe IBM Cloud infrastructure is designed to support the high-performance computing requirements of AI workloads, ensuring optimal performance, scalability, and reliability.

This section details the key network design considerations for AI applications in IBM Cloud.

![](image/watson-surround-pattern-networking.svg)
{: caption="Figure 2. Network Design in IBM Cloud" caption-side="bottom"}

**Virtual private Cloud (VPC)**

A Virtual Private Cloud (VPC) is a logically isolated network in an IBM Cloud account. A VPC provides a secure, dedicated environment for applications and data, with its own subnet, IP address range, and routing. This allows to deploy and manage applications in a highly flexible and scalable manner.


1. ***Management VPC***

A Management VPC is a specialized VPC that serves as the entry point for managing the IBM Cloud resources. It provides a secure, isolated network environment for managing the cloud resources, such as:

- Creating and managing VPCs
- Configuring network routes and subnets
- Monitoring and troubleshooting resource performance

The Management VPC is not intended for running applications, but rather serves as the control plane for managing the cloud infrastructure.

2. ***Workload VPC***

A Workload VPC is a production-grade VPC that can use to deploy and run applications. This VPC provides a scalable, high-performance environment for running various workloads, with features such as:

- Dedicated networking resources
- Support for multiple subnets and routing configurations
- Integration with IBM Cloud services, such as databases and message queues

Multiple Workload VPCs can be created to support different environments or applications, such as development, testing, and production.

3. ***Edge VPC***

An Edge VPC is a specialized VPC that provides low-latency, high-performance networking for edge computing workloads. Edge VPCs are designed to support IoT, AI, and other latency-sensitive applications that require direct access to the cloud. Key features of an Edge VPC include:
    
- Low-latency networking with reduced packet loss
- Support for multiple subnets and routing configurations
- Integration with IBM Cloud services, such as databases and message queues

Edge VPCs are ideal for deploying edge computing workloads, such as AI-powered camera systems or IoT devices that require real-time processing.

**Load Balancer**

A Load Balancer is responsible for distributing traffic across multiple instances of the AI application. They are designed to help in building resilient and scalable applications in IBM Cloud. 

4. ***IBM Cloud Load Balancer***

IBM Cloud Load Balancer is a managed service from IBM Cloud. This service is available in the cloud services catalogue. Some of the key features of this services are 

- HTTP/HTTPS traffic management: It can handle both HTTP and HTTPS traffic, ensuring secure communication between various application.
- TCP/UDP load balancing: It support TCP and UDP traffic, making me suitable for a wide range of applications
- Supports a variety of load-balancing methods, such as round robin, weighted round robin, and least connections
- Load balancing among virtual server and bare metal compute instances that reside locally within a data center
- Integration: Integrate with other IBM Cloud services like Watson and API Connect

For more details on the IBM Cloud Load Balancer refer to this [section in IBM Cloud Docs](https://cloud.ibm.com/docs/loadbalancer-service?topic=loadbalancer-service-about-ibm-cloud-load-balancer)
{: note}


**Gateway Services**

A Gateway is a set of managed services in IBM Cloud. They act as a bridge between client applications and the outside world, allowing to securely expose APIs, manage traffic, and enforce policies.

5. ***Transit Gateway***
A Transit Gateway is a managed network service that allows to simplify the network architecture and improve security by consolidating multiple networks into a single, highly available, and scalable platform.

It is essentially a hub-and-spoke architecture where multiple Virtual Private Clouds (VPCs) or Subnets can be connected to a central gateway. This enables communication between VPCs or Subnets without the need for individual VPN connections or peering configurations.

In this pattern, two Transit gateways are considered. One for the communication between the management, worker and edge VPCs and another one for the integration of on-premise network with IBM Cloud resources.


6. ***Gateway VPN***

A Gateway Virtual Private Network (VPN) is a service that enables to establish a secure, encrypted connection between the on-premises infrastructure and the IBM Cloud. This allows to extend the private network into the cloud, ensuring seamless communication between the internal resources and IBM Cloud-based services.

- Enables to connect the private network (e.g., client's data center or branch office) directly to the IBM Cloud without exposing any internal resources to the public internet.
- Reduces latency and improves performance by establishing a direct, optimized connection between the on-premises infrastructure and the IBM Cloud.
- IPsec: Supports IP Security Protocol (IPSec) for encrypting and authenticating traffic.
- MPLS: Supports Multiprotocol Label Switching (MPLS) for establishing a secure, managed connection between the on-premises infrastructure and the IBM Cloud.
- VPG: Virtual Private Gateway provides a secure entrance point for traffic from the on-premises infrastructure to the IBM Cloud.
- Supports connections with multiple cloud providers, allowing to use IBM Cloud alongside other clouds or networks.


7. ***Bastion Host***

A Bastion Host is a managed Linux-based virtual machine (VM) that serves as a secure entry point for accessing and managing other IBM Cloud resources.

- It acts as a single entry point for remote access to the cloud resources, such as virtual servers, databases, or storage systems.
- Users must authenticate with the Bastion Host using their IBM Cloud credentials (e.g., API keys, usernames, and passwords) before gaining access to other resources.
- The Bastion Host creates a secure network boundary between the cloud resources and external users or systems. This helps prevent unauthorized access or data exfiltration.


**Other Connection Services**

***8. VPN Connection***
A VPN (Virtual Private Network) connection for VPC enables to securely connect client's on-premises infrastructure or other clouds to the VPC over the internet. This provides a secure and encrypted tunnel between various networks.

- Connects IBM Cloud VPC to client's on-premise infrastructure, data centers, or other clouds (e.g., AWS, Azure) securely.
- Access IBM Cloud services, such as Kubernetes clusters, databases, or applications, from the on-premises environment.
- Migrate workloads between your VPC and on-premises infrastructure or other clouds.

In this pattern, the VPN connection is leveraged for accessing the IBM Cloud resoueces securely through a private connection over internet by system/cloud administrators, developer etc for various development and operational activities.

9. ***Direct Link 2.0***


10. ***Cloud Internet Service***

11. ***Virtual Private Endpoint (VPE)***
