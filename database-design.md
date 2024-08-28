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

The requirements for the database aspect for this pattern focus on the following:

* The database is required for customers x86 workloads on the cloud.
* The database is required for container workloads.
* The database is required for AI including RAG, chat, and image and video analysis.

## Database design considerations
{: #database-design-considerations}

In this section we cover two database aspects

* Enterprise generic database
* [AI database](/docs/watsonxdata?topic=watsonxdata-getting-started).
   * Presto
   * Milvus

### Enterprise application databases
{: #enterprise-app-databases}

The Enterprise or bespoke applications require a backend to store various entity data and their relations. Some of the essential aspects that an enterprise application would require include:

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

#### {{site.data.keyword.Bluemix_notm}} Databases for PostgreSQL
{: #postgresql-databases}

The database for PostgreSQL service provides a managed PostgreSQL database that can be used to store and retrieve data for the applications. This service allows you to easily deploy, manage, and scale your PostgreSQL databases without worrying about the underlying infrastructure. For more information, see [Getting started with Databases for PostgreSQL](/docs/databases-for-postgresql).

- Relational data storage: Store and manage large amounts of structured data, such as customer information, order history, or inventory levels.
- Application back-end: Use PostgreSQL as a back-end database for web applications, mobile apps, or IoT devices to store and retrieve data.
- Data warehousing: Build a data warehouse to analyze and report on large datasets, providing insights into business performance, customer behavior, or market trends.
- Analytics and reporting: Run complex analytics and reporting queries using PostgreSQL's advanced querying capabilities.
- IoT data processing: Store and process large volumes of IoT device sensor data, such as temperature readings or equipment performance metrics.
- Cloud-native applications: Build cloud-native applications that require high-performance, scalable, and reliable database services.
- Security and compliance: Meet security and compliance requirements by storing sensitive data in a highly secure and regulated database environment.

#### {{site.data.keyword.cloudantfull}}
{: #ibm-cloudant}

{{site.data.keyword.cloudantfull}} is a fully managed JSON document database that offers independent serverless scaling of provisioned throughput capacity and storage. {{site.data.keyword.cloudant_short_notm}} is compatible with Apache CouchDB and accessible through a simple to use HTTPS API for web, mobile, and IoT applications. For more information, see [Getting started with IBM Cloudant](/docs/Cloudant).

- JSON document-oriented: Store and retrieve data as JSON documents, making it easy to integrate with a wide range of programming languages and frameworks.
- High availability: Designed for 99.9% uptime, ensuring that the applications are always available and responsive.
- Scalable: Easily scale your database up or down to match changing business needs, without worrying about provisioning or managing the underlying infrastructure.
- Flexible data model: Store data in a flexible schema-less format, making it easy to adapt to changing requirements and integrate with other data sources.
- Customer service: Chatbots, virtual assistants, and automated customer support systems to enhance customer experience.

## Artificial intelligence database
{: #artificial-intelligence-database}


Enter [vectors](https://www.ibm.com/docs/en/essl/7.1). Vectors are arrays of numbers that can represent complex objects like words, images, videos, and audio, generated by a [machine learning](https://www.ibm.com/topics/machine-learning){: external} (ML) model. High-dimensional vector data is essential to machine learning, [natural language processing](https://www.ibm.com/topics/natural-language-processing){: external} (NLP) and other AI tasks. Some examples of vector data include:

* Text: Think about the last time that you interacted with a chatbot. How do they understand natural language? They rely on vectors, which can represent words, paragraphs and entire documents, that are converted through machine learning algorithms.
* Images: Image pixels can be described by numerical data and combined to make up a high-dimensional vector for that image.
* Speech and audio: Like images, sound waves can also be broken down into numerical data and represented as vectors, enabling AI applications such as voice recognition.

### Design considerations for Vector databases
{: #vector-databases}

Enterprises are increasingly favoring the [retrieval augmented generation (RAG)](https://research.ibm.com/blog/retrieval-augmented-generation-RAG){: external} approach in generative AI workflows for its faster time-to-market, efficient inference, and reliable output, particularly in key use cases such as customer care, HR, and talent. RAG helps ensure that the model is linked to the most current, reliable facts and that users have access to the model’s sources, so that its claims can be checked for accuracy. RAG is core to the ability to anchor large language models in trusted data to reduce model hallucinations.

This approach relies on using high-dimensional vector data to enrich prompts with semantically relevant information for in-context learning by foundation models. It requires effective storage and retrieval during the inference stage, which handles the highest volume of data. Vector databases excel at efficiently indexing, storing and retrieving these high-dimensional vectors, providing the speed, precision, and scale needed for applications like recommendation engines and chatbots.

### IBM watsonx.data with Milvus
{: #watsonx-milvus}

{{site.data.keyword.IBM_notm}} watsonx.data is an open, hybrid, and governed data store that includes the Milvus vector database. Milvus is designed specifically for handling high-dimensional vector data, making it ideal for tasks such as similarity search, recommendation systems, and other AI applications. For more information, see [IBM Watsonx.data and Milvus Integration](/docs/watsonxdata?topic=watsonxdata-adding-milvus-service).

The key features include: 

* High performance: Optimized for handling vector data with low-latency responses.
* Integration with {{site.data.keyword.IBM_notm}} watsonx.ai: Facilitates AI and machine learning projects by seamlessly integrating with IBM’s AI tools.
* Scalability: Can handle large volumes of vector data efficiently.
  Use cases: Retrieval augmented generation (RAG), semantic search, and AI-driven applications.
