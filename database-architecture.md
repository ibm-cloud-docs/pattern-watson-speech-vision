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

For building AI applications, there needs to be various databases for various requirements. Review the database architecture decisions for the speech and vision recognition with RAG AI pattern design based on functional aspects:


| Architecture decision                     | Requirement                                                                     | Alternative                                                                                                                                                | Decision                                                                   | Rationale                                                                                                                                                                                                                                                                                                                                                                                     |
| ----------------------------------------- | ------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Relational datastore | Provide a highly available backend database that meets availability, performance, and resiliency requirements for the application |* Database that is deployed on VSI and self-managed \n * Database for PostgreSQL \n * {{site.data.keyword.cloudantfull}} \n * SQL server | Database for PostgreSQL | A managed database that is highly available to store records across microservices. For this application, it uses [{{site.data.keyword.Bluemix_notm}} Databases for PostgreSQL](/docs/databases-for-postgresql?topic=databases-for-postgresql-getting-started&interface=ui) |
| Document datastore | Provide a document-based database optimized to store unstructured data for bespoke front end application |* Databases for PostgreSQL \n * Databases for MongoDB \n * Databases for Redis \n * {{site.data.keyword.cloudant_short_notm}} | {{site.data.keyword.cloudant_short_notm}} | {{site.data.keyword.cloudant_short_notm}} is available as an {{site.data.keyword.Bluemix_notm}}® service with a 99.99% SLA. {{site.data.keyword.cloudant_short_notm}} elastically scales throughput and storage, and its API and replication protocols are compatible with Apache CouchDB for hybrid or multicloud architectures.|
| Vector datastore | Provide a highly scalable vector data for Retrieval-Augmented Generation (RAG) application |* Pinecone \n * watsonx.data Milvus \n * ChromaDB | watsonx.data Milvus | Milvus is a vector database that stores, indexes, and manages massive embedding vectors that are developed by deep neural networks and other machine learning (ML) models. It is developed to empower embedding similarity search and AI application. Milvus makes unstructured data search more accessible and consistent across various environments.|
 {: caption="Table 1. Architecture decisions for databases" caption-side="bottom"} 
