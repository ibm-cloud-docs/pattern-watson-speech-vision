---
copyright:
  years: 2024
lastupdated: "2024-03-29"

subcollection: pattern-watson-speech-vision

keywords:
---
{{site.data.keyword.attribute-definition-list}}

# Storage design

{: #storage-design}

The following provides the details on various storage types and design for the watson speech to text, text to speech and image recognition use cases.

## Requirements

{: #storage-requirements}

For AI powered applications, it is essential to ensure that the underlying storage meets the following requirements

1. High-throughput storage: Speech-to-text & Vision recognition applications generate massive amounts of audio , Video analytical data, this needs high-throughput storage that can process large volumes of data quickly.
2. Low-latency access: To ensure real-time processing and minimize delays, the storage system must provide low-latency access to audio files.
3. Data compression and optimization: Effective compression techniques are essential for reducing the size of audio files while maintaining their integrity.
4. Scalability and reliability: As speech-to-text applications grow in popularity, the storage system must scale effortlessly to meet increasing demands while ensuring high availability.
5. Security and compliance: Robust security measures are essential to protect sensitive audio and text data from unauthorized access or breaches.
6. File synchronous transfer: ability to transfer large files from customer environment to {{site.data.keyword.Bluemix_notm}}.
7. All the storage for containers are stateless, as most of the applications data is stored in a database or in cloud object storage.

## Storage design considerations

{: #storage-considerations}

![img](image/watsonx-surround-pattern-storage.svg){: caption="Figure 10. Storage Design" caption-side="bottom"}

### {{site.data.keyword.Bluemix_notm}} Object Storage

{{site.data.keyword.Bluemix_notm}} Object storage provides a scalable and cost-effective way to store and manage large amounts of unstructured data.

1. Scalability: Store massive amounts of data with ease, as the capacity grows seamlessly with the usage.
2. Cost-Effectiveness: Pay only for what you use, reducing storage costs and minimizing waste.
3. High Availability: Ensure business continuity with built-in redundancy and disaster recovery capabilities.
4. Security: Data is protected by robust security features, including encryption at rest and in transit.
5. Easy Integration: Seamlessly integrates into existing cloud-based workflows using APIs and SDKs.

For the use cases described in this document, a large amount of data needs to be stored. This requires a cost effective and reliable storage solution. {{site.data.keyword.Bluemix_notm}} Object storage can store large files, such as videos, images, and audio recordings for processing, content delivery or archival purposes.

### {{site.data.keyword.Bluemix_notm}} Container Registry

{{site.data.keyword.Bluemix_notm}} Container Registry provides a highly available and scalable private image registry. This is a fully IBM managed service.

It includes automatic scanning of images and provides suggestions to fix potential vulnerabilities and protect the containers from being compromised.

### {{site.data.keyword.Bluemix_notm}} Block Storage

{{site.data.keyword.Bluemix_notm}} Block Storage is a scalable and highly available persistent storage service designed for modern cloud-native applications. Data is stored in fixed-size blocks, typically 4KB or 8KB in size. Each block is assigned a unique identifier (block number) and contains a specific amount of data.

1. Scalability: ability to scale up or down as needed.
2. High availability: ensure the data is always available with automatic replication across multiple Availability Zones.
3. Low latency: data is accessed with predictable and consistent performance.
4. Security: data is protected with end-to-end encryption, secure authentication, and authorization controls.
5. Integration: Seamlessly integrates with cloud-native applications using popular frameworks and APIs.

In containerized applications, block storage plays a crucial role as Persistent Volumes (PVs). By leveraging block storage as Persistent Volumes in containerized applications, data persistence is ensured, stateful application management is simplified, and storage resources can be scaled as needed.
