---
copyright:
  years: 2024
lastupdated: "2024-08-29"

subcollection: pattern-watson-speech-vision

keywords:
---
{{site.data.keyword.attribute-definition-list}}

# Architecture decisions for storage
{: #storage-decisions}

The following are the stroage architecture decisions for the speech and vision recognition with RAG AI.

## Storage architecture decision
{: #storage architecture decision}

| Architecture decision                                                           | Requirement                                                                                         | Options                                                                                                                  | Decision                 | Rationale                                                                                                                                                                                                                                                                                                                  |
| ------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------ | ------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Main storage for AI application                                                 | Provide highly available and efficient storage that meets the application performance requirements. | * VPC File Storage \n * VPC Block Storage \n * {{site.data.keyword.Bluemix_notm}} Object storage \n * {{site.data.keyword.redhat_openshift_notm}} Data Foundation \n * Portworx | VPC Block Storage        | VPC Block Storage provides high throughput and low-latency access to ensure real-time processing. It integrates easily with AI and machine learning (ML) frameworks.                                                                                                                                 |
| Container Registry                                                | Provide highly available and and scalable container registry to store the images used by {{site.data.keyword.redhat_openshift_notm}} workloads | * {{site.data.keyword.Bluemix_notm}} container registry\n * {{site.data.keyword.Bluemix_notm}} {{site.data.keyword.redhat_openshift_notm}} native container registry| {{site.data.keyword.Bluemix_notm}} container registry        | Highly available and scalable managed private container registry with advanced security and image vulnerability scanning. Native registry of {{site.data.keyword.Bluemix_notm}}.                                                                                                                          |
| Storage for large files, images, audio and video files                          | Reliably store and process various data formats for AI applications            | * VPC File Storage \n * VPC Block Storage\n * {{site.data.keyword.Bluemix_notm}} Object storage\n * {{site.data.keyword.redhat_openshift_notm}} Data Foundation\n * Portworx | {{site.data.keyword.Bluemix_notm}} Object Storage | {{site.data.keyword.Bluemix_notm}} Object storage is scalable, cost efficient, secure and easy to integrate. It stores data of any size or format as objects. {{site.data.keyword.Bluemix_notm}} Object storage can store large files, such as videos, images, and audio recordings, for processing, content delivery or archival purposes. |
{: caption="Table 1. Architecture decisions for storage" caption-side="bottom"}
