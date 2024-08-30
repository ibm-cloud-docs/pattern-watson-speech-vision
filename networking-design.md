---
copyright:
  years: 2024
lastupdated: "2024-08-28"

subcollection: pattern-watson-speech-vision

keywords:
---
{{site.data.keyword.attribute-definition-list}}

# Network design
{: #networking-design}

The following are the network design decisions for the speech and vision recognition with RAG AI pattern.

## Requirements
{: #requirements}

* The required environment must have connectivity to x86 virtualized workloads on the cloud
* The required environment must have connectivity to container workloads on the cloud
* There must be connectivity to AI services on {{site.data.keyword.Bluemix_notm}}
* There must be connectivity to all PaaS and Saas Services that are consumed on {{site.data.keyword.Bluemix_notm}}
* Ensure that there are secure connections to the Hybrid cloud environment
* Ensure that there are secure connections to external users and toward development pipeline to allow customer developer to write, integrate, and test code including delivering via a secured pipeline
* Ensure that there are serverless workloads on the cloud

## Network design considerations
{: #network-design-considerations}

For deploying AI applications, it's essential to design a robust and scalable network infrastructure that can handle the unique demands of these workloads. The {{site.data.keyword.Bluemix_notm}} infrastructure is designed to support the high-performance computing requirements of AI workloads, helping ensure optimal performance, scalability, and reliability.

The following section details the key network design considerations for AI applications in {{site.data.keyword.Bluemix_notm}}.

![Network design](image/watson-surround-pattern-networking.svg "Network design"){: caption="Figure 1. Network design for Watson Surround" caption-side="bottom"}

## Virtual private Cloud (VPC)
{: #vpc-considerations}

A Virtual Private Cloud (VPC) is a logically isolated network in an {{site.data.keyword.Bluemix_notm}} account. A VPC provides a secure, dedicated environment for applications and data, with its own subnet, IP address ranges, and routing. This allows for deploying and managing applications in a highly flexible and scalable manner.

### Management VPC
{: #management-vpc}

A Management VPC is a specialized VPC that serves as the entry point for managing the {{site.data.keyword.Bluemix_notm}} resources. It provides a secure, isolated network environment for managing the cloud resources.

The Management VPC is not intended for running applications, but rather serves as the control plane for managing the cloud infrastructure.
{: note}

### Workload VPC
{: #workload-vpc}

A workload VPC is a production-grade VPC that can be used to deploy and run applications. This VPC provides a scalable, high-performance environment for running various workloads.

Multiple Workload VPCs can be created to support different environments or applications, such as development, testing, and production.

### Application Load balancer
{: #load-balancer}

A load balancer is responsible for distributing traffic across multiple instances of the AI application. They are designed to help in building resilient and scalable applications.

For more information, see [About IBM Cloud Load Balancer](/docs/loadbalancer-service?topic=loadbalancer-service-about-ibm-cloud-load-balancer)

### Transit Gateway
{: #transit-gateway}

A Transit Gateway is a managed network service that allows to simplify the network architecture and improve security by consolidating multiple networks into a single, highly available, and scalable platform.

For more information, see [About IBM Cloud Transit Gateway](/docs/transit-gateway?topic=transit-gateway-about).

### VPN Gateway
{: #vpn-gateway}

A Virtual Private Network (VPN) Gateway is a service that enables to establish a secure, encrypted connection between the on-premises infrastructure and the {{site.data.keyword.Bluemix_notm}}.

In this pattern, a Site-to-Site VPN connection is used as a backup connection for accessing the {{site.data.keyword.Bluemix_notm}} resources securely through a private connection over internet by system/cloud administrators, developer and so on, for various development and operational activities in case the direct link connection becomes unavailable.

For more information, see [VPNs for VPC overview](/docs/vpc?topic=vpc-vpn-overview&interface=ui).

### Bastion host
{: #bastion-host}

A bastion host is a managed Linux-based virtual machine (VM) that serves as a secure entry point for accessing and managing other {{site.data.keyword.Bluemix_notm}} resources.

### Direct Link 2.0
{: #direct-link}

Direct Link 2.0 is a high-speed, and secure connectivity option that enables the client to establish a dedicated, always-on link between on-premises environments and {{site.data.keyword.Bluemix_notm}}.

For more information, see [About IBM Cloud Direct Link](https://cloud.ibm.com/docs/dl?topic=dl-dl-about).

### Cloud Internet Service
{: #cloud-internet-service}

Cloud Internet Services (CIS) is a suite of managed services that helps you optimize your internet presence and improve the performance of client's AI applications. CIS  provides a secure, scalable, and reliable way to deliver your content, applications, and APIs to users worldwide.

For more information, see [About IBM Cloud Internet Services](/docs/cis?topic=cis-about-ibm-cloud-internet-services-cis).

### Virtual Private Endpoint (VPE)
{: #cloud-vpe}
IBM Cloud Virtual Private Endpoints (VPE) for VPC enables to connect to supported IBM Cloud services from the VPC network by using the IP addresses of your choosing, which is allocated from a subnet within your VPC.

For more information, see [About virtual private endpoint gateways](https://cloud.ibm.com/docs/vpc?topic=vpc-about-vpe).

In this pattern, the Virtual Private Endpoint service is used to connect with various IBM Cloud services like DBaaS, watsonx services, Maximo SaaS, and others.
