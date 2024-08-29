---
copyright:
  years: 2024
lastupdated: "2024-08-29"

subcollection: pattern-watson-speech-vision

keywords:
---
{{site.data.keyword.attribute-definition-list}}

# Storage design

{: #storage-design}

The following provides the details on various storage types and design for the Watson speech to text, text to speech and image recognition use cases.

## Requirements

{: #storage-requirements}

For an AI-powered application, it's crucial to help ensure that the underlying storage meets the following requirements:

1. High-throughput storage: Speech to Text and vision recognition applications that generate massive amounts of audio and video analytical data. This needs high-throughput storage that can process large volumes of data quickly.
2. Low-latency access: To help ensure real-time processing and minimize delays, our storage system must provide low-latency access to audio files.
3. Data compression and optimization: Effective compression techniques are essential for reducing the size of audio files while maintaining their integrity.
4. Scalability and reliability: As Speech to Text applications grow in popularity, our storage system must scale effortlessly to meet increasing demands while helping ensure high availability.
5. Security and compliance: Robust security measures are essential to protect sensitive audio and text data from unauthorized access or breaches.
6. File synchronous transfer: The ability to transfer large files from customer environment to {{site.data.keyword.Bluemix_notm}}.
7. All the storage for containers is stateless, as most of the applications data is stored in DB.

## Storage design considerations
{: #storage-considerations}

![Storage design](image/watsonx-surround-pattern-storage.svg "Storage design"){: caption="Figure 10. Storage Design for Watson Surround" caption-side="bottom"}

### {{site.data.keyword.Bluemix_notm}} Object Storage
{: #cloud-ob-storage-watsonx}

{{site.data.keyword.Bluemix_notm}} Object storage provides a scalable and cost-effective way to store and manage large amounts of unstructured data.

1. Scalability: Store massive amounts of data with ease, as my capacity grows seamlessly with your needs.
2. Cost-effectiveness: Pay only for what you use, reducing storage costs and minimizing waste.
3. High availability: Help ensure business continuity with built-in redundancy and disaster recovery capabilities.
4. Security: Rest assured that your data is protected by robust security features, including encryption at rest and in transit.
5. Easy integration: Seamlessly integrate into your existing cloud-based workflows by using APIs and SDKs.

For this use case, there is a large volume of data that needs to be stored. This requires a cost-effective and reliable storage solution. {{site.data.keyword.Bluemix_notm}} Object storage can store large files, such as videos, images, and audio recordings, for processing, content delivery or archival purposes.

### {{site.data.keyword.Bluemix_notm}} Block Storage
{: #block-storage-watsonx}

{{site.data.keyword.Bluemix_notm}} Block Storage is a scalable and highly available persistent storage service that is designed for modern cloud-native applications. In this type of storage that stores data in fixed-size blocks, it's typically 4 KB or 8 KB in size. Each block is assigned a unique identifier (block number) and contains a specific amount of data.

1. Scalability: The ability to scale up or down as needed.
2. High availability: Ensure that your data is always available with automatic replication across multiple availability zones.
3. Low latency: Access your data quickly with predictable and consistent performance.
4. Security: Rest assured that your data is protected with end-to-end encryption, secure authentication, and authorization controls.
5. Integration: Seamlessly integrate with your cloud-native applications by using frameworks and APIs.

In containerized applications, Block Storage plays a crucial role as persistent volumes. By using Block Storage as persistent volumes in containerized applications, helps ensure the data persistence, simplify stateful application management, and scale your storage resources as needed.
