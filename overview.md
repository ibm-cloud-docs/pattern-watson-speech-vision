---
copyright:
  years: 2024
lastupdated: "2024-03-26"

subcollection: watsonx

keywords:
---

{{site.data.keyword.attribute-definition-list}}

# Overview

{: overview-id}

This pattern is focused on building enterprise AI environment with  watsonx architecture as the core on IBM Cloud along with other IBM Cloud services including IBM Cloud Roks, VPC, Maximo Visual Inspection, watson Voice assistance.
This pattern is helpfull for the enterprise customers in focusing on AI that needs to delivery RAG, Speech and image and video detection.

This patterns describes the architetcure based on the following key are technology

1.  watson x(software as service)
    1.  watson assistant
    2.  watson data.
    3.  watson governance
    4.  watson ai
2.  IBM Cloud VPC ROKS.
3.  IBM Cloud VPC VSI.
4.  IBM Cloud Devlopment Pipelines.
5.  Code Engine as service.
6.  Maximo visual Inspection as Services

## Overview of the overall solution

Overview of the Solution Architecture:

The solution architecture is designed to address specific needs within financial services through WatsonX AI deployment in a Software as a Service (SaaS) model. This architecture encompasses several key components that work together seamlessly to provide an end-to-end AI solution for enterprise clients. The following are the core elements of this ecosystem.


### ![](image/watsonx-surround-pattern-design-overview.drawio.svg)

### watson x deployment

A conversational AI model tailored for legal and insurance applications, this chatbot is built to support customers by automating routine tasks and extracting pertinent information from user inputs through advanced natural language processing (NLP) capabilities.

Standard watson deployment solution components.

watsonx Assistant – Used to conversation flow development and webchat interface watson Discovery – Used to ingest documents that will be used to retrieve relevant docs. watsonx ai – RAG with LLM and train as needed. \*watson orchestrate- workflows and integration(Dedicated)


### Retrieval-Augmented Generation (RAG)

The solution integrates with external data sources to provide a more comprehensive client experience by leveraging RAG technology for retrieving relevant documents and information from vast datasets, including vector databases like Milvus, hosted on ROKS.

### Enhanced User Experience with Watson Speech Assistance

Leveraging IBM's Watson Speech technology, the solution offers a sophisticated user interface that supports multiple languages, ensuring accessibility and convenience for end-users across different regions and linguistic backgrounds. The speech-to-text (STT) and text-to-speech (TTS) functionalities are hosted on Virtual Private Cloud (VPC) with GPU support to handle complex language models efficiently.

Clients can choose from different deployment options—simple, medium, or large—based on their specific production requirements. These options scale with the client's needs and provide a robust foundation for WatsonX Assistant development, document ingestion using Watson Discovery, and running complex Retrieval-Augmented Generation workflows with Large Language Models (LLM) within VPC. Speech to text and Text to speech with multi language support on VPC GPU. Speech summarization for users and virtual ai conversation.

### Application Development on IBM Cloud

The architecture leverages VPC Extensible and Kubernetes (ROKS) for application development that is both resilient and scalable. This enables businesses to deploy their workloads, including x86 and containerized applications, across a High Availability (HA) environment with an optional Disaster Recovery (DR) setup.

Multi-Region Deployment without DR: The WatsonX AI service is deployed across IBM Cloud Multi Region to ensure redundancy and failover capabilities, although a dedicated Disaster Recovery (DR) setup is not included in this configuration. This approach provides geographic diversity and helps maintain business continuity even in the event of regional disruptions.

The solution integrates with various IBM Cloud services to create a cohesive ecosystem:

1.  Vector Database solutions like Milvus, PostgreSql for RAG capabilities, hosted on ROKS.
2.  IBM Cloud Object Storage (COS) for storage needs.
3.  Block Storage to provide persistent disk storage.
4.  File Storage with Aspera integration for high-speed file transfers, such as uploading mp3, video files.
5.  Monitoring and Logging: The solution includes robust logging and monitoring capabilities through:
6.  IBM Cloud Activity Tracker for real-time activity monitoring within the cloud environment.
7.  IBM Cloud Logs to centralize logs from all services, aiding in troubleshooting and performance optimization.
8.  code engine.

### DevOps Pipeline

Deployment Lifecycle Management: The deployment lifecycle is managed using:

IBM Cloud Pipeline for automating development processes. IBM Cloud Registry for managing container images across different environments.

### Maximo Visual Inspection

This tool standardizes image scanning and document summarization, providing a consistent method for processing visual data within the claims process. It simplifies the extraction of relevant information from various sources, enhancing productivity and accuracy in claim handling.

Conclusion: The WatsonX AI solution on IBM Cloud offers an end-to-end platform tailored for financial services with a focus on AI capabilities. The architecture is designed to be scalable, secure, and highly available, ensuring that enterprises can leverage the latest advancements in AI without compromising on performance or reliability. With its comprehensive suite of tools and integration options, this solution stands ready to transform how financial institutions manage customer interactions, streamline claims processing, and maintain a vigilant watch against fraudulent activities.
