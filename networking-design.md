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

## Requirement

The requirements for the network aspect for this pattern focuses on the following:

* The required environment must have connectivity to x86 virtualized workloads on Cloud.
* The required environment must have connectivity to containizer workloads on Cloud.
* connectivity to AI services on {{site.data.keyword.Bluemix_notm}}.
* connectivity to all PaaS and Saas Services consuimed on {{site.data.keyword.Bluemix_notm}}.
* secure connections to Hybrid cloud environment.
* secure connections to external users and towards development pipeline to allow customer developer to write, integrate and test code including delivering via a secured pipeline.
* serverless workloads on cloud.

## Network Design considerations

For deploying AI applications, it's essential to design a robust and scalable network infrastructure that can handle the unique demands of these workloads. The {{site.data.keyword.Bluemix_notm}} infrastructure is designed to support the high-performance computing requirements of AI workloads, ensuring optimal performance, scalability, and reliability.

This section details the key network design considerations for AI applications in {{site.data.keyword.Bluemix_notm}}.

![Network Design in IBM Cloud](image/watson-surround-pattern-networking.svg){: caption="Figure 1. Network Design in {{site.data.keyword.Bluemix_notm}}" caption-side="bottom"}

## Virtual private Cloud (VPC)

A Virtual Private Cloud (VPC) is a logically isolated network in an {{site.data.keyword.Bluemix_notm}} account. A VPC provides a secure, dedicated environment for applications and data, with its own subnet, IP address ranges, and routing. This allows to deploy and manage applications in a highly flexible and scalable manner.

### 1. Management VPC

A Management VPC is a specialized VPC that serves as the entry point for managing the {{site.data.keyword.Bluemix_notm}} resources. It provides a secure, isolated network environment for managing the cloud resources, such as:

* Creating and managing VPCs
* Configuring network routes and subnets
* Monitoring and troubleshooting resource performance

The Management VPC is not intended for running applications, but rather serves as the control plane for managing the cloud infrastructure.

### 2. Workload VPC

A Workload VPC is a production-grade VPC that can be used to deploy and run applications. This VPC provides a scalable, high-performance environment for running various workloads, with features such as:

* Dedicated networking resources
* Support for multiple subnets and routing configurations
* Integration with {{site.data.keyword.Bluemix_notm}} services, such as databases and message queues

Multiple Workload VPCs can be created to support different environments or applications, such as development, testing, and production.

### 3. Load Balancer

A Load Balancer is responsible for distributing traffic across multiple instances of the AI application. They are designed to help in building resilient and scalable applications in {{site.data.keyword.Bluemix_notm}}.

{{site.data.keyword.Bluemix_notm}} Load Balancer for VPC is a managed service from {{site.data.keyword.Bluemix_notm}}. This service is available in the cloud services catalogue. Two types of load balancer for VPC are available: network load balancer (NLB) and appliacation load balancer (ALB).Some of the key features of this services are

* HTTP/HTTPS traffic management (Application Load Balancer only): It can handle both HTTP and HTTPS traffic, ensuring secure communication between various application.
* TCP/UDP load balancing (Network Load Balancer and Application Load Balancer): It support TCP and UDP traffic, making me suitable for a wide range of applications

For more details on the {{site.data.keyword.Bluemix_notm}} Load Balancer for VPC refer to this [section in {{site.data.keyword.Bluemix_notm}} Docs](https://cloud.ibm.com/docs/loadbalancer-service?topic=loadbalancer-service-about-ibm-cloud-load-balancer)
{: note}

### 4. Gateway Services

A Gateway is a set of managed services in {{site.data.keyword.Bluemix_notm}}. They act as a bridge between client applications and the outside world, allowing to securely expose APIs, manage traffic, and enforce policies.

#### Transit Gateway

A Transit Gateway is a managed network service that allows to simplify the network architecture and improve security by consolidating multiple networks into a single, highly available, and scalable platform.

For more details on the {{site.data.keyword.Bluemix_notm}} Transit Gateway refer to this [section in {{site.data.keyword.Bluemix_notm}} Docs](https://cloud.ibm.com/docs/transit-gateway?topic=transit-gateway-about)
{: note}

### 5. VPN Gateway

A Virtual Private Network (VPN) Gateway is a service that enables to establish a secure, encrypted connection between the on-premises infrastructure and the {{site.data.keyword.Bluemix_notm}}. This allows to extend the private network into the cloud, ensuring seamless communication between the internal resources and {{site.data.keyword.Bluemix_notm}}-based services.

{{site.data.keyword.Bluemix_notm}} VPN for VPC offers two types of VPN gateways:

* Site-to-Site gateways, based on the IPSec protocol
* Client-to-Site servers, based on OpenVPN

In this pattern, a Site-to-Site VPN connection is used as a backup connection for accessing the {{site.data.keyword.Bluemix_notm}} resources securely through a private connection over internet by system/cloud administrators, developer etc for various development and operational activities in case the direct link connection becomes unavailable.

For more details on the {{site.data.keyword.Bluemix_notm}} VPN for VPC refer to this [section in {{site.data.keyword.Bluemix_notm}} Docs](https://cloud.ibm.com/docs/vpc?topic=vpc-vpn-overview&interface=ui)
{: note}

### 6. Bastion Host

A Bastion Host is a managed Linux-based virtual machine (VM) that serves as a secure entry point for accessing and managing other {{site.data.keyword.Bluemix_notm}} resources.

* It acts as a single entry point for remote access to the cloud resources, such as virtual servers, databases, or storage systems.
* Users must authenticate with the Bastion Host using their {{site.data.keyword.Bluemix_notm}} credentials (e.g., API keys, usernames, and passwords) before gaining access to other resources.
* The Bastion Host creates a secure network boundary between the cloud resources and external users or systems. This helps prevent unauthorized access or data exfiltration.

### 7. Direct Link 2.0

Direct Link 2.0 is a high-speed, and secure connectivity option that enables client to establish a dedicated, always-on link between on-premises environments and {{site.data.keyword.Bluemix_notm}}. This direct connection eliminates the need for internet-based routing, reducing latency and improving overall performance.

Direct Link 2.0 is available in various regions worldwide, including the United States, Europe, Asia, and Latin America.

For more details on the {{site.data.keyword.Bluemix_notm}} Direct Link refer to this [section in {{site.data.keyword.Bluemix_notm}} Docs](https://cloud.ibm.com/docs/dl?topic=dl-dl-about)
{: note}

### 8. Cloud Internet Service

Cloud Internet Services (CIS) is a suite of managed services that helps you optimize your internet presence and improve the performance of client's AI applications. CIS  provide a secure, scalable, and reliable way to deliver your content, applications, and APIs to users worldwide.

For more details on the {{site.data.keyword.Bluemix_notm}} Internet Services refer to this [section in {{site.data.keyword.Bluemix_notm}} Docs](https://cloud.ibm.com/docs/cis?topic=cis-about-ibm-cloud-internet-services-cis)
{: note}

### 9. Virtual Private Endpoint (VPE)

{{site.data.keyword.Bluemix_notm}} Virtual Private Endpoints (VPE) for VPC enables to connect to supported {{site.data.keyword.Bluemix_notm}} services from the VPC network by using the IP addresses of your choosing, allocated from a subnet within your VPC.

For more details on the {{site.data.keyword.Bluemix_notm}} Virtual Private Endpoint refer to this [section in {{site.data.keyword.Bluemix_notm}} Docs](https://cloud.ibm.com/docs/vpc?topic=vpc-about-vpe)
{: note}

In this pattern, the Virtual Private Endpoint service is leveraged to connect with various {{site.data.keyword.Bluemix_notm}} services like DBaaS, Watsonx services, Maximo SaaS and others.
