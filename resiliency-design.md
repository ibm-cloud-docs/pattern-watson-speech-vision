---
copyright:
  years: 2024
lastupdated: "2024-03-29"

subcollection: pattern-watson-speech-vision

keywords:
---
{{site.data.keyword.attribute-definition-list}}

# Resiliency design

{: #resiliency-design-id}

## Requirements

{: #resiliency-requirements}

To ensure the resiliency of the solution as a whole, the following components must be taken into account:

- custom applications running on {{site.data.keyword.Bluemix_notm}} VPC's VSIs
- custom applications running on ROKS containers
- custom functions/applications/jobs running on {{site.data.keyword.Bluemix_notm}} Code Engine
- the SaaS services and in particular the AI related SaaS services (Watsonx, {{site.data.keyword.Bluemix_notm}} Speech to Text, Text to Speech) and especially the data they hold

## Considerations for High Availability

{: #ha-considerations}

### High Availability for IBM Watsonx services and} Software as a Service (SaaS) services

IBM Watson services, such as watsonx.ai, watsonx.data, watson Assistant for voice as well as {{site.data.keyword.Bluemix_notm}} Speech to Text, {{site.data.keyword.Bluemix_notm}} Text to Speech  are highly available services by default with no single point of failure. This is achieved by leveraging {{site.data.keyword.Bluemix_notm}} multi-zone regions.

More generally, every {{site.data.keyword.Bluemix_notm}} SaaS general availability (GA) offering is highly available with an SLA of 99,99%.

### High Availability for VPC

{{site.data.keyword.Bluemix_notm}} virtual server instances are highly available within the availability zone where they are deployed. If the original host of a VPC virtual server instance fails, the built in VPC host failure auto restart will automatically move the virtual server instance to a healthy host and restart it.

If cross availability zone high availability zone is needed, a more advanced design would be needed.
For instance, it can consist in a network or application load balancer distribuling traffic to VPC virtual server instances located in different availability zones of a VPC multi-zone region. Note that if the application running on the virtual server instances are not stateless, some kind of data synchronization mechanism will be needed between the virtual server instances.

### High Availability for ROKS

In a multi-zone region ROKS deployment, the openshift master and worker nodes are spread across 3 availability zones, making the ROKS containerized workloads highly available by default.

### High Availability for} Databases for PostgreSQL

Databases for PostgreSQL deployments contain a cluster with two data members, a leader and a replica. Both members contain a copy of the data by using asynchronous replication, with a distributed consensus mechanism to maintain cluster state and handle failovers. If the leader becomes unreachable, the cluster initiates a failover, and the replica is promoted to leader. The replica rejoins the cluster and your cluster continues to operate normally. Additional read replicas can be added in a different availability zone in the same region or in a different region to further increase high availability.

### High Availability for IBM Cloudant

All data is stored in triplicate across three separate physical servers in a cluster within a region. Cloudant instances can be provisioned in multiple regions and setup with continuous data replication to provide High Availability across regions.

### High Availability for IBM Cloud Code Engine

IBM Cloud Code Engine is based on {{site.data.keyword.Bluemix_notm}} Kubernetes Service clusters. When provisioning an {{site.data.keyword.Bluemix_notm}} Code engine project, the workload is deployed in a single availability zone of the multi-zone region that was selected. If a failure in the hosting availability zone occurs, the workload is automatically recreated in one of the remaining zone.
