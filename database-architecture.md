---
copyright:
  years: 2024
lastupdated: "2024-08-15"

subcollection: pattern-watson-speech-vision

keywords:
---
{{site.data.keyword.attribute-definition-list}}

# Architecture decisions for database
{: #ad-database}

For building AI application there needs a variety of databases for various requirements. Review the database architecture decisions for the Red Hat OpenShift on VPC cluster design  based on functional aspects:


| Architecture decision                     | Requirement                                                                     | Alternative                                                                                                                                                | Decision                                                                   | Rationale                                                                                                                                                                                                                                                                                                                                                                                     |
| ----------------------------------------- | ------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Relational Datastore |Provide highly available backend database that meets availability, performance & resilliency requirements for the application|* Database deployed on VSI and self-managed\n * Database for PostgreSQL \n * IBM Cloudant \n * SQL Server|Database for PostgreSQL|A managed database that is highly available to store records across microservices. For this application, it uses [{{site.data.keyword.Bluemix_notm}} Databases for PostgreSQL](https://cloud.ibm.com/docs/databases-for-postgresql?topic=databases-for-postgresql-getting-started&interface=ui){: external} \n|
|Document Datastore|Provide document based database optimised to store unstructured data for bespoke frontend application|* Databases for PostgreSQL\n * Databases for MongoDB \n * Databases for Redis \n * IBM Cloudant| IBM Cloudant | IBM® Cloudant® is available as an {{site.data.keyword.Bluemix_notm}}® service with a 99.99% SLA. Cloudant elastically scales throughput and storage, and its API and replication protocols are compatible with Apache CouchDB for hybrid or multicloud architectures.|
|Vector Datastore |Provide a highly scalable vector data for RAG application|* Pinecone\n * watsonx.data (Milvus)\n * ChromaDB| watsonx.data (Milvus) | Milvus is a vector database that stores, indexes, and manages massive embedding vectors that are developed by deep neural networks and other machine learning (ML) models. It is developed to empower embedding similarity search and AI applications. Milvus makes unstructured data search more accessible and consistent across various environments.|
 {: caption="Table 1. Architecture decisions for databases" caption-side="bottom"} 
