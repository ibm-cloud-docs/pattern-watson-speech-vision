---
copyright:
  years: 2024
lastupdated: "2024-03-28"

subcollection: pattern-watson-speech-vision

keywords:
---
{{site.data.keyword.attribute-definition-list}}

# Architecture decisions for networking for watsonx VPC, ROKS and watson STT

{: #networking}

## Network Architecture decision

{: #ad-network}

| **Architecture decision**                                                 | **Requirement**                                                                                | **Options**                                                                                                        | **Decision**                      | **Rationale**                                                                                                                                                                                  |
| ------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------ | --------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Public DNS  | Provide DNS resolution to support the use of hostnames instead of IP addresses for applications | - IBM Cloud Internet Services (CIS)  \n -  IBM Cloud DNS                                                                        | IBM Cloud Internet Services (CIS)                  | IBM Cloud Internet Services support provisioning and configuring DNS records for public DNS resolution and can be integrated with the public VPC ALBs for the web tier. |
| Application Load Balancer                                                                 | Route web user http/https requests                           | - VPC ALB \n -  VPC NLB  \n -  HA proxy on VSI | VPC ALB | VPC ALB is recommended for web-based workloads. * Provides layer 4 and layer 7 load-balancing\n * Supports HTTP, HTTPS, and TCP requests\n * Supports SSL offloading.\n                                    |
|VPC to VPC Connectivity|Connect two or more VPCs over a private network|- VPC peering\n - Local Transit Gateway\n - Global Transit Gateway|Local Transit Gateway (TGW)|The Local Transit Gateway enables connectivity between the Management, Workload & Edge VPCs.|
|Connectivity to Cloud Services|Provide secure connection to Cloud Services|- VPC Gateway and Virtual Private Endpoints (VPE)\n - Private Cloud Service endpoints\n - Public Cloud Service Endpoints\n|Virtual Private Endpoints (VPE)|VPC Gateway and Virtual Private Endpoints enable connectivity to IBM Cloud services by using private IP addresses allocated from a VPC subnet.|
|Connectivity for remote management of resources|Provide secure and encrypted connectivity to the cloud’s private network for management purposes.|* Client VPN for VPC \n * VPN for VPC \n * Direct Link| VPN for VPC | VPN for VPC allows remote devices to securely connect to the VPC network. The management of IBM Cloud resources happen remotely through a private connection by the operations team.|
|Network segmentation and isolation of various workloads|* Deploy workloads in an isolated environment based on their nature\n * Provide fine grained policies for the information flow across segments.|* Virtual Private Clouds (VPCs)\n *Subnets\n *Security Groups (SGs)\n *ACLs|VPCs|VPCs provide secure, virtual networks for various tiers of the application, which are logically isolated from other public cloud tenants. The fine grained information policy flow can achieved through appropriate security groups (SG) & Access Control Lists (ACLs) |
|Connectivity from On-Premise to IBM Cloud |Provide private connectivity for the on-Premise enterprise applications to be integrated semmelesly to the systems running in IBM Cloud| * Site to site VPN Connection\n * Client to Site VPN Connection \n * Direct Link \n | Direct Link | Direct Link is a high-speed, and secure connectivity option that enables client's to establish a dedicated, always-on link between the on-premises and IBM Cloud.|
 {: caption="Table 1. Architecture decisions for network" caption-side="bottom"} 
