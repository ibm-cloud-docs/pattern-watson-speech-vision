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

The following provides the details on various storage types and design for the watsonx speech to text, text to speech and image recognition use case.

## Requirements

{: #storage-requirements}


For an AI powered applications, its crucial to ensure that the underlying storage should meet the following requirements

1. High-throughput storage: Speech-to-text & Vision recognition applications that generate massive amounts of audio , Video analytical data, this needs high-throughput storage that can process large volumes of data quickly.
2. Low-latency access: To ensure real-time processing and minimize delays, our storage system must provide low-latency access to audio files.
3. Data compression and optimization: Effective compression techniques are essential for reducing the size of audio files while maintaining their integrity.
4. Scalability and reliability: As speech-to-text applications grow in popularity, our storage system must scale effortlessly to meet increasing demands while ensuring high availability.
5. Security and compliance: Robust security measures are essential to protect sensitive audio and text data from unauthorized access or breaches.
6. Integration with AI/ML frameworks: Easy integration with popular AI and machine learning (ML) frameworks is vital for developing innovative applications that leverage speech-to-text and text-to-speech capabilities.

## Considerations

{: #storage-considerations}

![](image/watsonx-surround-pattern-storage.svg)
{: caption="Figure 3. Storage Design" caption-side="bottom"}

***IBM Cloud Object Storage***

IBM Cloud Object storage provides a scalable and cost-effective way to store and manage large amounts of unstructured data.

1. Scalability: Store massive amounts of data with ease, as my capacity grows seamlessly with your needs.
2. Cost-Effectiveness: Pay only for what you use, reducing storage costs and minimizing waste.
3. High Availability: Ensure business continuity with built-in redundancy and disaster recovery capabilities.
4. Security: Rest assured that your data is protected by robust security features, including encryption at rest and in transit.
5. Easy Integration: Seamlessly integrate me into your existing cloud-based workflows using APIs and SDKs.

For the usecase, there will be a large volume of data needs to be stored. This requires a cost effective and reliable storage solution. IBM Cloud Object storage can store large files, such as videos, images, and audio recordings, for processing, content delivery or archival purposes.

***IBM Cloud Block Storage***

IBM Cloud Block Storage are a scalable and highly available persistent storage service designed for modern cloud-native applications. In this type of storage that stores data in fixed-size blocks, typically 4KB or 8KB in size. Each block is assigned a unique identifier (block number) and contains a specific amount of data.

1. Scalability: Store up to 16 TiB (terabytes) per volume, with the ability to scale up or down as needed.
2. High availability: Ensure your data is always available with automatic replication across multiple Availability Zones.
3. Low latency: Access your data quickly with predictable and consistent performance.
4. Security: Rest assured that your data is protected with end-to-end encryption, secure authentication, and authorization controls.
5. Integration: Seamlessly integrate me with your cloud-native applications using popular frameworks and APIs.

In containerized applications, block storage plays a crucial role as Persistent Volumes (PVs).
Here are some key points for this use cases:

- Data Persistence: Containers can be restarted or deleted without affecting the underlying data stored on a persistent volume.
- Shared Storage: Multiple containers can access and share data stored in a single persistent volume, enabling collaboration and communication between containers.
- Stateful Applications: Persistent volumes help maintain the state of stateful applications, ensuring that critical data is retained even after container restarts or crashes.

By leveraging block storage as Persistent Volumes in containerized applications, ensures the data persistence, simplify stateful application management, and scale your storage resources as needed.

***File Storage Aspera addition***

In IBM Cloud , Aspera is a high-speed transfer technology that enables fast, reliable, and secure movement of large files between locations. It's particularly useful for transferring massive amounts of data, such as those associated with media and entertainment industries.

Aspera works by creating a temporary, optimized copy of your file and then transmitting it to its destination using standard protocols like HTTP or FTP. This process allows for much faster transfer speeds than traditional methods, making it ideal for situations where you need to move large files quickly, such as:

- File sharing: Aspera enables fast and secure sharing of large files across the cloud.
- Data migration: It helps simplify the process of migrating massive amounts of data from one location to another.
- Content delivery: Aspera accelerates the delivery of high-bandwidth content, such as movies or TV shows.

By combining Aspera's high-speed transfer capabilities with the scalability, durability, and security of IBM Cloud file storage services, you can efficiently move and manage large amounts of data in the cloud.
