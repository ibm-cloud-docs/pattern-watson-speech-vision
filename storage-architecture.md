---
copyright:
  years: 2024
lastupdated: "2024-03-29"

subcollection: pattern-watson-speech-vision

keywords:
---
{{site.data.keyword.attribute-definition-list}}

# Architecture decisions for storage( Siva/Dwarka)

{: #storage-decisions}

Siva please check if Sppech reqyures us to storage for audio, same is the case for maximo.

## Storage Architecture decision

{: #storage architecture decision}

| Architecture decision                                                           | Requirement                                                                                         | Options                                                                                                                  | Decision                 | Rationale                                                                                                                                                                                                                                                                                                                  |
| ------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------ | ------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Main storage for AI spplication                                                 | Provide highly available and efficient storage that meets the application performance requirements. | * VPC File Storage\n * VPC Block Storage\n * IBM Cloud Object storage\n * Red Hat OpenShift Data Foundation\n * Portworx | VPC Block Storage        | VPC Block Storage provides high throughput, low-latency access to ensure real-time processing and minimize delays. This is easy to integrate with AI and machine learning (ML) frameworks.                                                                                                                                 |
| Storage for large files, images, audio and video files                          | Storage for reliably storing and processing variuos data formates for the AI application            | * VPC File Storage\n * VPC Block Storage\n * IBM Cloud Object storage\n * Red Hat OpenShift Data Foundation\n * Portworx | IBM Cloud Object Storage | IBM Cloud Object storage is a scalable, cost effective, secure and easy to integrate. This is flexible to storage the any size, volume or formate of data as objects. IBM Cloud Object storage can store large files, such as videos, images, and audio recordings, for processing, content delivery or archival purposes. |
| {: caption="Table 2. Architecture decisions for storage" caption-side="bottom"} |                                                                                                     |                                                                                                                          |                          |                                                                                                                                                                                                                                                                                                                            |
