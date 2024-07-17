---
copyright:
  years: 2024
lastupdated: "2024-03-29"

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

**VSI GPU for specific LLM and Watson studio**

### Architecture components

{: #architecture-components}

**VPC**

**ROKS**

Code Engine

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
