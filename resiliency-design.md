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

To ensure the resiliency of the solution, the following components must be taken into account:

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

### Disaster Recovery 
