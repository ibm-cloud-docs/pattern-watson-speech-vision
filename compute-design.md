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

## Requirements
{: #compute-requirements}

**VPC**


**ROKS design**


### Architecture components
{: #architecture-components}

**VPC**

A Virtual Private Cloud (VPC) is a logically isolated network in an IBM Cloud account. A VPC provides a secure, dedicated environment for applications and data, with its own subnet, IP address range, and routing. This allows to deploy and manage applications in a highly flexible and scalable manner.

***Management VPC***

A Management VPC is a specialized VPC that serves as the entry point for managing the IBM Cloud resources. It provides a secure, isolated network environment for managing the cloud resources, such as:

  - Creating and managing VPCs
  - Configuring network routes and subnets
  - Monitoring and troubleshooting resource performance

The Management VPC is not intended for running applications, but rather serves as the control plane for managing the cloud infrastructure.

***Workload VPC***

A Workload VPC is a production-grade VPC that can use to deploy and run applications. This VPC provides a scalable, high-performance environment for running various workloads, with features such as:

  - Dedicated networking resources
  - Support for multiple subnets and routing configurations
  - Integration with IBM Cloud services, such as databases and message queues

Multiple Workload VPCs can be created to support different environments or applications, such as development, testing, and production.

***Edge VPC***

An Edge VPC is a specialized VPC that provides low-latency, high-performance networking for edge computing workloads. Edge VPCs are designed to support IoT, AI, and other latency-sensitive applications that require direct access to the cloud. Key features of an Edge VPC include:

  - Low-latency networking with reduced packet loss
  - Support for multiple subnets and routing configurations
  - Integration with IBM Cloud services, such as databases and message queues

Edge VPCs are ideal for deploying edge computing workloads, such as AI-powered camera systems or IoT devices that require real-time processing.


**ROKS**

**Code Engine**

IBM Cloud Code Engine is a fully managed, serverless platform built on kubernetes designed to run event-driven functions, batch jobs or containerized applications/microservices. Code Engine can also build applications from source code.

Code Engine resources (application, jobs and functions) are organized in projects which are regional.

Some of the main advantages of IBM Cloud Code Engine are:

- fully integrated into IBM Cloud, allowing to take advantage of all the IBM Cloud services through service bindings.

- cost effective, applications, jobs are run on demand or on schedule and can scale, even down to zero.

- event-driven applications that can react to messages received from various sources (Cloud Object Storage, Cron, Kafka, webhooks) through subscriptions and perform actions based on them

- native DDoS protection for traffic coming from the internet through the use of IBM Cloud Internet Services (CIS) by default

- private workloads over a shared underlying infrastructure, projects and their entities are isolated from each other, private source code repositories and private image registries can be used

Code Engine allows to build cost effective modern event driven applications and let developers focus on the code, not worrying about the platform needed to run it.

Speech to Text hosting requirements.

1. A VPC Landing Zone is deployed which provides the ability to automate the installation of an Red Hat OpenShift cluster into a multizone region.
2. Three separate clusters are created for the production, pre-production, and dev and test environments. The diagram depicts only the production cluster.
3. Separate worker pools are created within the clusters for the application and storage workloads.
4. The worker pool node size and quantity are determined based on the resource requirements for the application and storage workloads.
5. To meet the Red Hat OpenShift on VPC service availability Service Level Agreement (SLA) of 99.99%, a minimum of 6 worker nodes are equally distributed across three availability zones.
6. Total worker node capacity is sized at 150% of the total workload's required capacity, so that if one zone fails, the resources are available to maintain the workload.
7. By default, the cluster is provisioned with a VPC security group and a cluster-level security group.
8. The Red Hat OpenShift platform is integrated with {{site.data.keyword.Bluemix_notm}}d Services to provide centralized cluster observability services.
9.
