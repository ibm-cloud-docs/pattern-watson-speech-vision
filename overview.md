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

This pattern provides an overview and a foundation for building an enterprise artificial intelligence (AI) environment using the Watsonx architecture as the core for AI and integration with other IBM Cloud services. 
It combines watsonx with IBM Cloud ROKS, Virtual Private Cloud (VPC), Maximo Visual Inspection, and Watson Voice Assistance to deliver AI solutions that meets RAG, real-time analytics, speech recognition, image and video detection.
This pattern is helpful for the enterprise customers in focusing on AI that needs to delivery RAG, Speech and image and video detection. 
This pattern describes how can a customer host and run x86 on IBM Cloud VPC and container workloads on IBM Cloud ROKS VPC in close proximity to watson x environment delivery all in one enterprise solution.

This pattern is built upon the following key technologies:

1. Watson X: a software-as-a-service (SaaS) offering for building AI-powered applications
2. Watson Assistant: a cloud-based AI platform for developing conversational interfaces( speech to text and text to speech)
3. Watson Data: a managed data service that enables secure and scalable data storage
4. Watson Governance: a set of tools for managing and governing Watson-powered AI solutions
5. Watson AI: a portfolio of AI technologies, including natural language processing (NLP), machine learning (ML), and computer vision (CV)
6. IBM Cloud VPC ROKS: a cloud-based infrastructure service that enables scalable and secure deployment of applications
7. IBM Cloud VPC VSI: a virtual server instance for running custom workloads on IBM Cloud
8. IBM Cloud Development Pipelines: a continuous integration/continuous delivery (CI/CD) toolchain for automating software development workflows
9. Code Engine as-a-Service: a cloud-based service that enables rapid application development and deployment using containerized applications
10. Maximo Visual Inspection as-a-Service: an AI-powered inspection solution for detecting defects in images and videos


## Overview of the overall solution

Overview of the Solution Architecture:

The solution architecture is designed to address specific needs within enterprise customer who need AI RAG, with Chat capability for Speech and voice itneraction with the internal application to deal with documents and also provide ability for image and video recognition for variour functional and non functional requirements. this is achieved by WatsonX AI deployment in a Software as a Service (SaaS) model. This architecture encompasses several key components that work together seamlessly to provide an end-to-end AI solution for enterprise clients. The following are the core elements of this ecosystem.

![](image/Overview-Pattern.svg){: caption="Figure 1. Functional overview of the watsonx AI and IBM Cloud surround environment" caption-side="bottom"}

1 Customer Datacenter location: A physical or virtual data center where customers can host their own infrastructure on IBM Cloud.

2 End users: The individuals who will be using applications, services, and data hosted in an IBM Cloud environment.

3 Compute on IBM Cloud through VPC/ROKS: Enables the deployment of compute workloads into a Virtual Private Cloud (VPC) or Red Hat OpenShift (ROKS), providing isolation and security for cloud-based infrastructure.

4 Watson X services: A set of cognitive computing capabilities, such as natural language processing, computer vision, and machine learning, designed to help organizations solve complex problems through AI-powered insights. Provides Retrieval Augmentation Generation (RAG) to do Text Retrieval and Text Generation allowing users to interact with documents.

5 Enhanced user experience via Watson STT and TTS: Improves the way humans interact with machines by leveraging IBM Watson's Speech-to-Text (STT) and Text-to-Speech (TTS) capabilities for more natural language-based interfaces.

6 Maximo Visual Inspection: A visual inspection feature within Maximo, an asset management platform, that enables users to capture and analyze video evidence of equipment or facility conditions, streamlining maintenance workflows and decision-making processes.

7 Application run time services: Offers a range of cloud-based services for deploying, managing, and optimizing application workloads in real-time, ensuring optimal performance, scalability, and security across IBM Cloud environments.

8 Apps Life Cycle Management: A comprehensive platform for designing, building, testing, deploying, and maintaining applications throughout their entire life cycle within an IBM Cloud environment.

9 Storage: Provides scalable and secure cloud storage services to help customers efficiently store, manage, and retrieve large amounts of data across various types of workloads.

11  Security and compliance: Offers a suite of security solutions designed to protect customer data in transit and at rest, ensuring compliance with major industry standards for confidentiality, integrity, and availability.

12  Logging and monitoring: Enables customers to collect, analyze, and visualize log data from their cloud-based applications and infrastructure, providing insights into system performance, usage patterns, and potential issues that need attention.

### IBM Cloud watsonx Service

The watsonx as service on IBM Cloud integrates with external data sources to provide a more comprehensive client experience by leveraging RAG technology for retrieving relevant documents and information from vast datasets, including vector databases like Milvus and customer apps hosted on ROKS.governance is a key functionality of the watson offering allowing a proper administrative control over the utilization and management of watsonx ai components.

Standard watson deployment solution components considered 
1.  watson x(software as service)
    1.  watson assistant
    2.  watson data.
    3.  watson governance
    4.  watson ai

watsonx Assistant – Used to conversation flow development and webchat interface watson Discovery – Used to ingest documents that will be used to retrieve relevant docs. 
watsonx ai – RAG with LLM and train as needed. 
watson orchestrate- workflows and integration(Dedicated) if needed.

### Enhanced User Experience with Watson Speech Assistance

Leveraging IBM's Watson Speech technology, the solution offers a sophisticated user interface that supports multiple languages, ensuring accessibility and convenience for end-users across different regions and linguistic backgrounds. The speech-to-text (STT) and text-to-speech (TTS) functionalities are hosted on IBM Cloud.

### Application Development on IBM Cloud

The architecture leverages IBM Cloud VPC and IBM Cloud ROKS for application development that is both resilient and scalable. This enables businesses to deploy their workloads, including x86 and containerized applications, across a High Availability (HA) environment across MZR( Multi-Zone Region)

The solution integrates with various IBM Cloud services to create a cohesive ecosystem:

1.  IBM Cloud Object Storage (COS) for storage needs.
2.  Block Storage to provide persistent disk storage.
3.  File Storage with Aspera integration for high-speed file transfers, such as uploading mp3, video files.
4.  Monitoring and Logging: The solution includes robust logging and monitoring capabilities through:
5.  Code engine: Customer can run event triggered events as functions as needed.

### DevOps Pipeline

Deployment Lifecycle Management: The deployment lifecycle is managed using:

IBM Cloud Pipeline for automating development processes. IBM Cloud Registry for managing container images across different environments.

### Maximo Visual Inspection

This tool standardizes image scanning and document summarization, providing a consistent method for processing visual data within the claims process. It simplifies the extraction of relevant information from various sources, enhancing productivity and accuracy in claim handling.

Conclusion: The WatsonX AI solution on IBM Cloud offers an end-to-end platform tailored for financial services with a focus on AI capabilities. The architecture is designed to be scalable, secure, and highly available, ensuring that enterprises can leverage the latest advancements in AI without compromising on performance or reliability. With its comprehensive suite of tools and integration options, this solution stands ready to transform how financial institutions manage customer interactions, streamline claims processing, and maintain a vigilant watch against fraudulent activities.
