---
copyright:
  years: 2024
lastupdated: "2024-08-28"

subcollection: pattern-watson-speech-vision

keywords:
---
{{site.data.keyword.attribute-definition-list}}

# Compute design
{: #compute-design}

The following are the compute design considerations for the speech and vision recognition with RAG AI pattern.

## Requirement
{: #compute-requirement}

The requirements for the compute aspect for this pattern focus on the following:

* The compute required to host x86 workloads on Cloud.
* The compute required to host container workloads.
* Development pipeline to allow customer developer to write, integrate and test code including delivering via a secured pipeline.
* Serverless workloads on cloud.

## Compute solution architecture
{: #compute-solution}

Customers who want to take advantage of the extended watsonx capabilities should also consider how to integrate these capabilities with their existing applications. By hosting their traditional x86 or containerized  applications on {{site.data.keyword.Bluemix_notm}} virtual private cloud (VPC) VSIs or containers running on {{site.data.keyword.redhat_openshift_notm}} on VPC, latency between IBM watsonx services and the customer is minimized, increasing the performances and responsiveness of the customer's application.

1. {{site.data.keyword.Bluemix_notm}} virtual private cloud (VPC) {{site.data.keyword.redhat_openshift_notm}}
2. {{site.data.keyword.Bluemix_notm}} virtual private cloud (VPC) virtual server instance (VSI)
3. {{site.data.keyword.Bluemix_notm}} devlopment pipelines
4. {{site.data.keyword.Bluemix_notm}} Code Engine

This also allows the customer to benefit from the flexibility and scalability of {{site.data.keyword.Bluemix_notm}} VPC offerings and gain easy access all the associated {{site.data.keyword.Bluemix_notm}} services.

### Architecture components
{: #architecture-components}

![Compute design](image/watsonx-surround-pattern-{{site.data.keyword.redhat_openshift_notm}}.svg "Compute design"){: caption="Figure 1. Compute design for Watson Surround" caption-side="bottom"}

1. A workload VPC landing zone provisioned to deploy various client workloads.
2. Workloads are deployed across multiple availability zones to meet any high availability requirements.
3. Network ACL in each zone define rules controlling inbound and outbound traffic within a VPC.
4. Any containerized workloads are deployed on the {{site.data.keyword.redhat_openshift_notm}} on VPC service.
   * a minimum of 6 worker nodes are equally distributed across three availability zones.
   * By default, the cluster is provisioned with a VPC security group and a cluster-level security group.
   * Control plane nodes and components are managed by {{site.data.keyword.Bluemix_notm}} in {{site.data.keyword.redhat_openshift_notm}} Kubernetes service on {{site.data.keyword.Bluemix_notm}}.
   * The AI applications are deployed as microservices and exposed through OpenShift routes, making them easier to integrate with other systems or services.
   * Separate worker pools are created within the clusters for the application and storage workloads.
   * The worker pool node size and quantity are determined based on the resource requirements for the application and storage workloads.

For more details on the {{site.data.keyword.redhat_openshift_notm}} capacity planning for various workloads refer to this [section in IBM Cloud Docs](https://cloud.ibm.com/docs/pattern-webapp-openshift-vpc?topic=pattern-webapp-openshift-vpc-compute-design#sizing-your-environment)
{: note}

5. Virtual Server Instances (VSIs) offer a powerfull way to deploy, manage, and scale your applications in {{site.data.keyword.Bluemix_notm}}.
6. {{site.data.keyword.vpe_fullt}}s (VPE) enables private access to {{site.data.keyword.Bluemix_notm}} services, like {{site.data.keyword.Bluemix_notm}} object storage or databases without having to route traffic through the internet.
7. An application load balancer balances the incoming traffic across the availability zones and ensures that the cloud based applications are highly available, scalable and performant.
8. {{site.data.keyword.Bluemix_notm}} Code Engine is used for any serverless workloads.

### IBM Cloud Code Engine
{: #ibm-code-engine}

{{site.data.keyword.Bluemix_notm}} Code Engine is a fully managed, serverless platform built on Kubernetes designed to run event-driven functions, batch jobs, or containerized applications and microservices. Code Engine can also build applications from source code. Code Engine resources (application, jobs and functions) are organized in projects which are regional.
