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

- custom applications running on IBM Cloud VPC's VSIs
- custom applications running on ROKS containers
- custom functions/applications/jobs running on IBM Cloud Code Engine
- the SaaS services and in particular the AI related SaaS services (Watsonx, IBM Cloud Speech to Text, Text to Speech, Maximo Visual inspection) and especially the data they hold

## Considerations for High Availability

{: #ha-considerations}

### High Availability for IBM watsonx services

### High Availability for VPC

IBM Cloud virtual server instances are highly available within the availability zone where they are deployed. If the original host of a VPC virtual server instance fails, the built in VPC host failure auto restart will automatically move the virtual server instance to a healthy host and restart it.

If cross availability zone high availability zone is needed, a more advanced design would be needed.
For instance, it can consist in a network or application load balancer distribuling traffic to VPC virtual server instances located in different availability zones of a VPC multi-zone region. Note that if the application running on the virtual server instances are not stateless, some kind of data synchronization mechanism will be needed between the virtual server instances.

### High Availability for ROKS

In a multi-zone region ROKS deployment, the openshift master and worker nodes are spread across 3 availability zones, making the ROKS containerized workloads highly available by default.

### High Availability for IBM Cloud Databases for PostgreSQL

Databases for PostgreSQL deployments contain a cluster with two data members, a leader and a replica. Both members contain a copy of the data by using asynchronous replication, with a distributed consensus mechanism to maintain cluster state and handle failovers. If the leader becomes unreachable, the cluster initiates a failover, and the replica is promoted to leader. The replica rejoins the cluster and your cluster continues to operate normally. Additional read replicas can be added in a different availability zone in the same region or in a different region to further increase high availability.

### High Availability for IBM Cloudant

All data is stored in triplicate across three separate physical servers in a cluster within a region. Cloudant instances can be provisioned in multiple regions and setup with continuous data replication to provide High Availability across regions.

### High Availability for IBM Cloud Code Engine

IBM Cloud Code Engine is based on IBM Cloud Kubernetes Service clusters. When provisioning an IBM Cloud Code engine project, the workload is deployed in a single availability zone of the multi-zone region that was selected. If a failure in the hosting availability zone occurs, the workload is automatically recreated in one of the remaining zone.

### High Availability for SaaS services

IBM Cloud Speech to Text, Text to Speech and Maximo Visual Inspection are highly available services by default with no single point of failure. This is achieved by leveraging IBM Cloud multi-zone regions.

More generally, every IBM Cloud SaaS general availability (GA) offering is highly available with an SLA of 99,99%.

## Considerations for Disaster Recovery

{: #dr-considerations}

### Disaster Recovery for IBM watsonx services

### Disaster Recovery for IBM Cloud VPC Virtual Servers Instances

IBM Cloud VPC virtual server instances and their storage are tied to the availability zone where they are deployed (where they are highly available).

To be able to restore IBM Cloud VPC virtual server instances when a disaster affects an IBM Cloud availability zone or a region, regular backups should be taken.

The native IBM Cloud Backup for VPC service allows to automatically create backups and manually restore Block Storage for VPC volumes. It is based on the IBM Cloud snapshots for VPC service.

Block storage backup snapshots can be copied from one region to another region, and that snapshot can be used to restore a volume in the new region. Boot volumes are supported, meaning that a new instance can be directly created from a backup snapshot.

For more information regarding IBM Cloud backup for VPC, see [Backup for VPC] (https://cloud.ibm.com/docs/vpc?topic=vpc-backup-service-about&interface=ui).

### Disaster Recovery for ROKS

To protect Red Hat Openshift on IBM Cloud workloads against an IBM Cloud multi-zone region (MZR) wide failure, several clusters need to be deployed in different IBM Cloud regions and be exposed via a global load balancer such as IBM Cloud Internet Services (CIS).

For the global load balancer to detect if one of the clusters is unavailable, consider adding a ping-based health check to every IP address. When you set up this check, your DNS provider regularly pings the IP addresses that you added to your domain. If one IP address becomes unavailable, then traffic is not sent to this IP address anymore. However, Red Hat OpenShift does not automatically restart pods from the unavailable cluster on worker nodes in available clusters.

In this pattern the applications running on the ROKS cluster are considered as being stateless. As a result storage replication between ROKS clusters deployed in different regions is not needed.

### Disaster Recovery for IBM Cloud Databases for PostgreSQL

As part of the service, a daily backup of the database is automatically taken. The backup is stored  in a cross-region Object Store instance. Additional manual backup can also be performed. In case of unavailability of the original IBM Cloud region, the backup can be restored to a new instance of IBM Cloud Databases for PostgreSQL.

### Disaster Recovery for IBM Cloudant

IBM Cloudant data isn't automatically backed up, but supported tools are provided to handle backups.
In addition, provisioning Cloudant instances in different IBM Cloud regions and configuring bidirectional replication between them allows to quickly recover to the latest state in case a disaster makes a region unavailable.

### Disaster Recovery for IBM Cloud Code Engine

To protect Code Engine workloads against an IBM Cloud multi-zone region (MZR) wide failure, the workloads should be deployed across multiple MZRs and implement an automatic failover mechanism by leveraging an Edge Proxy service such as IBM Cloud Internet Services (CIS). For more information about deploying an application across multiple regions, see [Deploying code engine workloads across multiple regions](https://cloud.ibm.com/docs/codeengine?topic=codeengine-deploy-multiple-regions).

### Disaster Recovery for IBM Cloud SaaS Services

For the IBM Cloud SaaS services used in this solution, the focus should be on preserving the data through an appropriate backup strategy.

In the unlikely event of an IBM Cloud  multi-zone region failure, the services remain available in other multi-zone regions. Therefore the steps to recover from the failure would be to create new services instances in another multi-zone region and then to restore the data that was previously backed up to these new services instances.

#### Disaster Recovery for IBM Cloud Speech to Text

Your disaster recovery plan includes knowing, preserving, and being prepared to restore all data that is maintained on IBM Cloud. This includes data from custom language models, custom acoustic models, and asynchronous speech recognition requests.

Re-creating custom models, especially custom acoustic models, from saved data can take a significant amount of time. Maintaining parallel service configurations in multiple locations can eliminate the turnaround time associated with disaster recovery.

For custom language models, you need to maintain and be prepared to re-create and restore your custom language models and their corpora, grammars, and custom words. You also need to be prepared to retrain your custom language models on their data and words resources.

#### Disaster Recovery for IBM Cloud Text to Speech

For the Text to Speech service, only data for custom models, custom words, speaker models, and custom prompts is stored on IBM Cloud. Your disaster recovery plan includes knowing, preserving, and being prepared to restore your customization information.

Preserve the following information about your custom models, custom entries, speaker models, and custom prompts:

- A list of all of your custom models and their definitions
- Information about all custom entries (word/translation pairs) in your custom models
- A list of all of your speaker models and their definitions. To list information about your speaker models
- Information about all custom prompts in your custom models

It is a best practice to preserve this information in a format that you can use to re-create your customized resources in the event of a failure. Actively maintaining the information, and preparing the calls listed in the following section ahead of time, can enable you to recover as quickly as possible.
