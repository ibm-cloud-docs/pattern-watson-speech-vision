---
copyright:
  years: 2024
lastupdated: "2024-07-25"

subcollection: pattern-watson-speech-vision

keywords:
---
{{site.data.keyword.attribute-definition-list}}

# Compute design

{: #compute-design}

## Requirement

The requirements for the compute aspect for this pattern focuses on the following:

* The compute required hosting x86 workloads on Cloud.
* The compute required to host container workloads.
* Development pipeline to allow customer developer to write, integrate and test code including delivering via a secured pipeline.
* serverless workloads on cloud.

## Compute solution architecture

Customers who want to take advantage of the extended watsonx capabilities should also consider how to integrate these capabilities with their existing applications.

By hosting their traditional x86 or containerized  applications on IBM Cloud VPC VSIs or containers running on Red Hat OpenShift on VPC, latency between IBM watsonx services and the customer is minimized, increasing the performances and responsiveness of the customer's application.

1. IBM Cloud VPC ROKS.
2. IBM Cloud  VPC VSI.
3. IBM Cloud Devlopment Pipelines.
4. Code Engine.

This also allows the customer to benefit from the flexibility and scalability of IBM Cloud VPC offerings and gain easy access all the associated IBM Cloud services.

### Architecture components

{: #architecture-components}

![](image/watsonx-surround-pattern-ROKS.svg)
{: caption="Figure 3. Deployment of ROKS in cloud" caption-side="bottom"}

1. A Workload VPC Landing Zone provisioned to deploy various client workloads.
2. The workloads are deployed across multiple availability zones to meet any high availability requirements.
3. The Subnet ACL in each zone is to define rules for controlling inbound and outbound traffic with in a VPC.
4. Any containerised workloads are deployed on the Red Hat OpenShift on VPC service
5. - To meet the Red Hat OpenShift on VPC service availability Service Level Agreement (SLA) of 99.99%, a minimum of 6 worker nodes are equally distributed across three  availability zones.
   - Total worker node capacity is sized at 150% of the total workload's required capacity, so that if one zone fails, the resources are available to maintain the workload.
   - By default, the cluster is provisioned with a VPC security group and a cluster-level security group.
   - The Red Hat OpenShift platform is integrated with {{site.data.keyword.Bluemix_notm}}d Services to provide centralized cluster observability services.
   - Three separate clusters are created for the production, pre-production, and dev and test environments. The diagram depicts only the production cluster.
6. Virtual Server Instances (VSIs) offer a powerfull way to deploy, manage, and scale your applications in IBM Cloud.
7. Any containerised workloads are deployed on the Red Hat OpenShift on VPC service
8. Virtual Server Instances (VSIs) offer a powerfull way to deploy, manage, and scale your applications in IBM Cloud.

>>>>>>> e44e374e042a5865db317e966310e89c315bb185
>>>>>>>
>>>>>>
>>>>>
>>>>
>>>
>>

6. The Virtual Private Endpoint (VPE) enables to access IBM Cloud services, like cloud storage or databases without having to route traffic through the internet.
7. An Application Load balancer balances the incoming traffic across the availability zones and ensures that the cloud based applications are highly available, scalable and performant.
8. IBM Cloud Code Engine is used for any serverless workloads.

### **Red Hat OpenShift on VPC**

1. Master / Control Plane nodes and components are managed by IBM Cloud in Red Hat OpenShift Kubernetes service on IBM Cloud.
2. The GenAI applications are deployed as microservices and expoed via OpenShift routes, making them easier to integrate with other systems or services.
3. Three separate clusters are created for the production, pre-production, and dev and test environments. The diagram depicts only the production cluster.
4. Separate worker pools are created within the clusters for the application and storage workloads.
5. The worker pool node size and quantity are determined based on the resource requirements for the application and storage workloads.
6. By default, the cluster is provisioned with a VPC security group and a cluster-level security group.
7. To meet the Red Hat OpenShift on VPC service availability Service Level Agreement (SLA) of 99.99%, a minimum of 6 worker nodes are equally distributed across three availability zones.
8. The worker / Data Plane nodes capacity is sized at 150% of the total workload's required capacity, so that if one zone fails, the resources are available to maintain the workload.

For more details on the ROKS capacity planning for various workloads refer to this [section in IBM Cloud Docs](https://cloud.ibm.com/docs/pattern-webapp-openshift-vpc?topic=pattern-webapp-openshift-vpc-compute-design#sizing-your-environment)
{: note}

9. The Red Hat OpenShift platform is integrated with IBM Cloudd Services to provide centralized cluster observability services.

### **IBM Cloud Code Engine**

IBM Cloud Code Engine is a fully managed, serverless platform built on kubernetes designed to run event-driven functions, batch jobs or containerized applications/microservices. Code Engine can also build applications from source code.

Code Engine resources (application, jobs and functions) are organized in projects which are regional.

The key advantages of IBM Cloud Code Engine are:

- fully integrated into IBM Cloud, allowing to take advantage of all the IBM Cloud services through service bindings.
- cost effective, applications, jobs are run on demand or on schedule and can scale, even down to zero.
- event-driven applications that can react to messages received from various sources (Cloud Object Storage, Cron, Kafka, webhooks) through subscriptions and perform actions based on them
- native DDoS protection for traffic coming from the internet through the use of IBM Cloud Internet Services (CIS) by default
- private workloads over a shared underlying infrastructure, projects and their entities are isolated from each other, private source code repositories and private image registries can be used

Code Engine allows to build cost effective modern event driven applications and let developers focus on the code, not worrying about the platform needed to run it.
