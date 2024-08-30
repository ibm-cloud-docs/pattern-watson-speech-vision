---
copyright:
  years: 2024
lastupdated: "2024-08-29"

subcollection: pattern-watson-speech-vision

keywords:
---
{{site.data.keyword.attribute-definition-list}}

# Resiliency design
{: #resiliency-design-id}

## Requirements
{: #resiliency-requirements}

To ensure the resiliency of the solution, the following components must be taken into account:

- Custom applications running on {{site.data.keyword.Bluemix_notm}} VPC's VSIs
- Custom applications running on {{site.data.keyword.redhat_openshift_notm}} containers
- Custom functions,applications, and jobs running on {{site.data.keyword.Bluemix_notm}} Code Engine
- The SaaS services, particularly the AI related SaaS services such as watsonx, {{site.data.keyword.Bluemix_notm}} Speech to Text, Text to Speech and the data they hold

## Considerations for High Availability
{: #ha-considerations}

### High Availability for IBM Watsonx services and Software as a Service (SaaS) services
{: #ha-considerations-ibm-watsonx}

IBM Watson services, such as watsonx.ai, watsonx.data, {{site.data.keyword.conversationshort}} for voice as well as {{site.data.keyword.Bluemix_notm}} Speech to Text, {{site.data.keyword.Bluemix_notm}} Text to Speech  are highly available services by default with no single point of failure. This is achieved by leveraging {{site.data.keyword.Bluemix_notm}} multi-zone regions.

More generally, every {{site.data.keyword.Bluemix_notm}} SaaS general availability (GA) offering is highly available with an SLA of 99.99%.

### High Availability for VPC
{: #ha-considerations-vpc}

{{site.data.keyword.Bluemix_notm}} virtual server instances are highly available within the availability zone where they are deployed. If the original host of a VPC virtual server instance fails, the built in VPC host failure auto restart will automatically move the virtual server instance to a healthy host and restart it.

If cross availability zone high availability zone is needed, a more advanced design would be needed.
For instance, it can consist in a network or application load balancer distribuling traffic to VPC virtual server instances located in different availability zones of a VPC multi-zone region. Note that if the application running on the virtual server instances are not stateless, some kind of data synchronization mechanism will be needed between the virtual server instances.

### High Availability for {{site.data.keyword.redhat_openshift_notm}}
{: #ha-considerations-roks}

In a multi-zone region {{site.data.keyword.redhat_openshift_notm}} deployment, the {{site.data.keyword.redhat_openshift_notm}} master and worker nodes are spread across 3 availability zones, making the {{site.data.keyword.redhat_openshift_notm}} containerized workloads highly available by default.

### High Availability for {{site.data.keyword.Bluemix_notm}} Databases for PostgreSQL
{: #ha-considerations-postgre}

Databases for PostgreSQL deployments contain a cluster with two data members, a leader and a replica. Both members contain a copy of the data by using asynchronous replication, with a distributed consensus mechanism to maintain cluster state and handle failovers. If the leader becomes unreachable, the cluster initiates a failover, and the replica is promoted to leader. The replica rejoins the cluster and your cluster continues to operate normally. Additional read replicas can be added in a different availability zone in the same region or in a different region to further increase high availability.

### High Availability for {{site.data.keyword.Bluemix_notm}} Databases for Elasticsearch
{: #ha-considerations-elasticsearch}

Databases for Elasticsearch provides replication, fail-over, and high-availability features to protect your databases and data from infrastructure maintenance, upgrades, and failures. Deployments contain a cluster with three data nodes where any node can be the primary node. If one data member becomes unreachable, your cluster continues to operate normally. If more nodes go down and the cluster can't maintain a quorum, it becomes read-only to protect your data. The cluster resumes normal operations when the nodes are recovered or new nodes are added.

When an index is added to Elasticsearch, the data is split into shards that are spread across the nodes in the cluster. This allows to run concurrent operations on data across all the nodes. Not all shards contain a complete copy of all the data in the index. To enforce that multiple complete copies of the data are spread across the cluster in a node failure, you should ensure that when you create an index you set the replica count to at least 1. Setting the replica count to 0 can cause data loss.

### High Availability for IBM Cloudant
{: #ha-considerations-ibm-cloudant}

All data is stored in triplicate across three separate physical servers in a cluster within a region. Cloudant instances can be provisioned in multiple regions and setup with continuous data replication to provide High Availability across regions.

### High Availability for {{site.data.keyword.Bluemix_notm}} Code Engine
{: #ha-considerations-code-engine}

{{site.data.keyword.Bluemix_notm}} Code Engine is based on {{site.data.keyword.Bluemix_notm}} Kubernetes Service clusters. When provisioning an {{site.data.keyword.Bluemix_notm}} Code engine project, the workload is deployed in a single availability zone of the multi-zone region that was selected. If a failure in the hosting availability zone occurs, the workload is automatically recreated in one of the remaining zone.
