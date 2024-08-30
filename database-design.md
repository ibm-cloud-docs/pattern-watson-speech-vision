---
copyright:
  years: 2024
lastupdated: "2024-08-29"

subcollection: pattern-watson-speech-vision

keywords:
---
{{site.data.keyword.attribute-definition-list}}

# Database design
{: #database-design}

The following are the database design considerations for the speech and vision recognition with RAG AI pattern.

## Database requirements
{: #database-design-requirements}

The requirements for the database aspect for the speech and vision recognition with RAG AI pattern focus on the following:

* The database is required for customers x86 workloads on the cloud.
* The database is required for container workloads.
* The database is required for AI including RAG, chat, and image and video analysis.

## Enterprise application databases considerations
{: #enterprise-app-databases}

The Enterprise or bespoke applications require a backend database  to store various entity data and their relations. Some of the essential aspects that an enterprise application would require include:

- Scalability: The database must be able to scale horizontally by adding more nodes and vertically by increasing the processing power as the application grows.
- High availability: The database must help ensure high availability by providing features like replication, load balancing, and automatic failover if node failure occurs.
- Security: The database must provide robust security features, including:
  * Authentication and authorization controls
  * Data encryption both at rest and in transit
  * Access control lists (ACLs) to restrict data access
- Performance: The database must be able to handle high volumes of read and write operations while maintaining low latency and high throughput.
- Data consistency: The database must help ensure data consistency across all nodes and replicas, with features like multi-version concurrency control and snapshot isolation.
- Backup and recovery: The database must provide robust backup and recovery mechanisms to help ensure business continuity if unexpected failures or errors occur.
- Compliance: The database must comply with relevant industry regulations and standards, such as GDPR, HIPAA, PCI-DSS, and SOX.

### IBM Cloud PostgreSQL
{: #postgresql-databases}

The database for PostgreSQL service provides a managed PostgreSQL database that can be used to store and retrieve data for the applications. This service allows you to easily deploy, manage, and scale your PostgreSQL databases without worrying about the underlying infrastructure. For more information, see [Getting started with Databases for PostgreSQL](/docs/databases-for-postgresql). This pattern considers utilizing PostgreSQL for the environment.

### IBM Cloud Elasticsearch
{: #ibm-elasticsearch}

[Elasticsearch](https://www.elastic.co/elasticsearch){: external} is an open source search and analytics engine based on the Apache Lucene library. This is used to store vector representations  also known as embeddings created by using machine learning algorithms.

### {{site.data.keyword.cloudantfull}}
{: #ibm-cloudant}

{{site.data.keyword.cloudantfull}} is a fully managed JSON document database that offers independent serverless scaling of provisioned throughput capacity and storage. This is a NOSQL database required for storing sessions for application which are stateless in nature. {{site.data.keyword.cloudant_short_notm}} is compatible with Apache CouchDB and accessible through a simple to use HTTPS API for web, mobile, and IoT applications. For more information, see [Getting started with IBM Cloudant](/docs/Cloudant).

## Design considerations for Vector databases
{: #vector-databases}

Enterprises are increasingly favoring the [retrieval augmented generation (RAG)](https://research.ibm.com/blog/retrieval-augmented-generation-RAG){: external} approach in generative AI workflows for its faster time-to-market, efficient inference, and reliable output, particularly in key use cases such as customer care, HR and talent. RAG helps ensure that the model is linked to the most current, reliable facts and that users have access to the model’s sources, so that its claims can be checked for accuracy. RAG is core to the ability to anchor large language models in trusted data to reduce model hallucinations.

### IBM watsonx.data with Milvus
{: #watsonx-milvus}

{{site.data.keyword.IBM_notm}} watsonx.data is an open, hybrid, and governed data store that includes the Milvus vector database. Milvus is designed specifically for handling high-dimensional vector data, making it ideal for tasks such as similarity search, recommendation systems, and other AI applications. For more information, see [IBM Watsonx.data and Milvus Integration](/docs/watsonxdata?topic=watsonxdata-adding-milvus-service).
