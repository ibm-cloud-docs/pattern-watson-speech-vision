---
copyright:
  years: 2024
lastupdated: "2024-03-29"

subcollection: pattern-watson-speech-vision

keywords:
---
{{site.data.keyword.attribute-definition-list}}

# Resiliency design(Bertrand)

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

### High Availability for VPC

IBM Cloud virtual server instances are highly available within the availability zone where they are deployed. If the original host of a VPC virtual server instance fails, the built in VPC host failure auto restart will automatically move the virtual server instance to a healthy host and restart it.

If cross availability zone high availability zone is needed, a more advanced design would be needed.
For instance, it can consist in a network or application load balancer distribuling traffic to VPC virtual server instances located in different availability zones of a VPC multi-zone region. Note that if the application running on the virtual server instances are not stateless, some kind of data synchronization mechanism will be needed between the virtual server instances.

### High Availability for ROKS

In a multi-zone region ROKS deployment, the openshift master and worker nodes are spread across 3 availability zones, making the ROKS containerized workloads highly available by default.

### High Availability for IBM Cloud Code Engine

IBM Cloud Code Engine is based on IBM Cloud Kubernetes Service clusters. When provisioning an IBM Cloud Code engine project, the workload is deployed in a single availability zone of the multi-zone region that was selected. If a failure in the hosting availability zone occurs, the workload is automatically recreated in one of the remaining zone.

### High Availability for SaaS services

IBM Cloud Speech to Text, Text to Speech and Maximo Visual Inspection are highly available services by default with no single point of failure. This is achieved by leveraging IBM Cloud multi-zone regions.

More generally, every IBM Cloud SaaS general availability (GA) offering is highly available with an SLA of 99,99%.

## Considerations for Disaster Recovery

{: #dr-considerations}

#### Disaster Recovery for IBM Cloud VPC Virtual Servers Instances

IBM Cloud VPC virtual server instances and their storage are tied to the availability zone where they are deployed (where they are highly available).

To be able to restore IBM Cloud VPC virtual server instances when a disaster occurs in an availability zone or a region, regular backups should be taken.

The native IBM Cloud Backup for VPC service allows to automatically create backups and manually restore Block Storage for VPC. The backup activity can be scheduled and use tags to identify the volumes to backup.

In case of an IBM Cloud multi-zone

#### Disaster Recovery for ROKS

To protect Red Hat Openshift on IBM Cloud workloads against an IBM Clou multi-zone region (MZR) wide failure, several clusters need to be deployed in different IBM Cloud regions and be exposed via a global load balancer such as IBM Cloud Internet Services (CIS). 

For the global load balancer to detect if one of the clusters is unavailable, consider adding a ping-based health check to every IP address. When you set up this check, your DNS provider regularly pings the IP addresses that you added to your domain. If one IP address becomes unavailable, then traffic is not sent to this IP address anymore. However, Red Hat OpenShift does not automatically restart pods from the unavailable cluster on worker nodes in available clusters.

If the workloads are stateful, particular attention should also be given to storage replication between the clusters running in different regions.
Several options exist for cross region replication such as Portworx or IBM Cloud Object Storage. The choice of a storage option depends mainly on the specific requirements in terms of RPO/RTO and performances.

#### Disaster Recovery for IBM Cloud Code Engine

To protect Code Engine workloads against an IBM Clou multi-zone region (MZR) wide failure, the workloads should be deployed across multiple MZRs and implement an automatic failover mechanism by leveraging an Edge Proxy service such as IBM Cloud Internet Services (CIS). For more information about deploying an application across multiple regions, see [Deploying code engine workloads across multiple regions](https://cloud.ibm.com/docs/codeengine?topic=codeengine-deploy-multiple-regions).

#### Disaster Recovery for IBM Cloud SaaS Services

For the IBM Cloud SaaS services used in this solution, the focus should be on preserving the data through appropriate backups.

In the unlikely event of an IBM Cloud  multi-zone region failure, the services remain available in other multi-zone regions. Therefore the steps to recover from the failure would be to create new services instances in another multi-zone region and then to restore the data that was previously backedup to these new services instances.

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

