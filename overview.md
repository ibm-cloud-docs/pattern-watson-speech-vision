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

## Pattern insight

1. This pattern provides an overview and a foundation for building an enterprise artificial intelligence (AI) environment using the Watsonx architecture as the core for AI and integration with other IBM Cloud services. It combines Watsonx with IBM Cloud ROKS, Virtual Private Cloud (VPC), Maximo Visual Inspection, and Watson Voice Assistance to deliver AI solutions that meets RAG, real-time analytics, speech recognition, image and video detection.
2. This pattern is helpful for the enterprise customers in focusing on AI that needs to delivery RAG, Speech and image and video detection.
3. This pattern describes how can a customer host and run x86 on IBM Cloud VPC and container workloads on IBM Cloud ROKS VPC in close proximity to Watsonx environment delivery all in one enterprise solution.

## Industry use cases
{: usecase-id}

Here are pratical use case implementation across industry for watsonx and Maximo visual inspection with watson voice assistance.

1. Financial/Insurance claims enhancement : 
   1. Use Maximo Visual Inspection as-a-Service in conjunction with IBM Cloud VPC ROKS to develop a insurance claim system. 
   2. Analyze video feeds to detect anomalies, help in claims processing and generate reports for approver. Help end users to provide a proper search, RAG and voice interaction with documents, images, videos.

2. Healthcare industry usecases: 
   1. Use Watsonx to build an AI-powered application that analyzes medical images (e.g., MRI, CT scans) for disease detection and diagnosis. 
   2. Integrate Maximo Visual Inspection as-a-Service to enable real-time image analysis and generate reports.
   3. Use cameras installed on medical equipment (e.g., MRI machines) or in storage areas to capture images of devices.
   4. Apply computer vision algorithms to analyze the images and detect signs of wear, damage, or malfunction in real-time.
   5. Integrate with RAG and voice to provide better user experience 
   
3. Chatbot-based Customer Support: 
   1. Implement Watson Assistant to create a conversational interface for customer support chatbots.
   2. Provide voice and RAG implementation with documents for end customer with speech to text and text to speech.

4. Quality Control for Manufacturing
   1. Use computer vision to inspect products (e.g., parts, components) as they move along a production line.
   2. Detect defects or irregularities in real-time using AI-powered image analysis.
   3. Provide immediate feedback to manufacturing personnel, enabling them to correct issues on the spot and reduce waste.
   4. Integrate with RAG and voice to provide better user experience

5. Asset Inspection for Oil & Gas
   1. Utilize unmanned aerial vehicles (UAVs) or drones equipped with cameras to capture images of oil rigs, pipelines, or other assets.
   2. Employ AI-powered image analysis to detect signs of wear, damage, or malfunction in real-time.
   3. Integrate with RAG and voice to provide better user experience

This pattern is built upon the following key technologies:

1. Watsonx: a software-as-a-service (SaaS) offering for building AI-powered applications
2. Watson Assistant: a cloud-based AI platform for developing conversational interfaces( speech to text and text to speech)
3. watson.data: a managed data service that enables secure and scalable data storage
4. watson.governance: a set of tools for managing and governing watson-powered AI solutions
5. watson.ai: a portfolio of AI technologies, including natural language processing (NLP), machine learning (ML), and computer vision (CV)
6. IBM Cloud VPC ROKS: a cloud-based infrastructure service that enables scalable and secure deployment of applications
7. IBM Cloud VPC VSI: a virtual server instance for running custom workloads on IBM Cloud
8. IBM Cloud Development Pipelines: a continuous integration/continuous delivery (CI/CD) toolchain for automating software development workflows
9. Code Engine as-a-Service: a cloud-based service that enables rapid application development and deployment using containerized applications
10. Maximo Visual Inspection as-a-Service: an AI-powered inspection solution for detecting defects in images and videos



## Solution Overview

Overview of the Solution Architecture:

The solution architecture is designed to address specific needs within enterprise customer who need AI RAG, with Chat capability for Speech and voice interaction with the bespoke client application to deal with documents injestion and also provide ability for image and video recognition for variour functional and non functional requirements. This is achieved by watsonx ai deployment in a Software as a Service (SaaS) model. This architecture encompasses several key components that work together seamlessly to provide an end-to-end AI solution for enterprise clients. The following are the core elements of this ecosystem.

![](image/Overview-Pattern.svg){: caption="Figure 1. Functional overview of the watsonx ai and IBM Cloud surround environment" caption-side="bottom"}

1 Customer Datacenter location: A physical or virtual data center where customers can host their own infrastructure on IBM Cloud.

2 End users: The individuals who will be using applications, services, and data hosted in an IBM Cloud environment.

3 Compute on IBM Cloud through VPC/ROKS: Enables the deployment of compute workloads into a Virtual Private Cloud (VPC) or Red Hat OpenShift (ROKS), providing isolation and security for cloud-based infrastructure. 

4 watson services: A set of cognitive computing capabilities, such as natural language processing, computer vision, and machine learning, designed to help organizations solve complex problems through AI-powered insights. Provides Retrieval Augmentation Generation (RAG) to do Text Retrieval and Text Generation allowing users to interact with documents.

5 Enhanced user experience via watson STT and TTS: Improves the way humans interact with machines by leveraging IBM watson's Speech-to-Text (STT) and Text-to-Speech (TTS) capabilities for more natural language-based interfaces.

6 Maximo Visual Inspection: A visual inspection feature within Maximo, an asset management platform, that enables users to capture and analyze video evidence of equipment or facility conditions, streamlining maintenance workflows and decision-making processes.

7 Application run time services: Offers a range of cloud-based services for deploying, managing, and optimizing application workloads in real-time, ensuring optimal performance, scalability, and security across IBM Cloud environments.

8 Apps Life Cycle Management: A comprehensive platform for designing, building, testing, deploying, and maintaining applications throughout their entire life cycle within an IBM Cloud environment.

9 Storage: Provides scalable and secure cloud storage services to help customers efficiently store, manage, and retrieve large amounts of data across various types of workloads.

10  Security and compliance: Offers a suite of security solutions designed to protect customer data in transit and at rest, ensuring compliance with major industry standards for confidentiality, integrity, and availability.

11  Logging and monitoring: Enables customers to collect, analyze, and visualize log data from their cloud-based applications and infrastructure, providing insights into system performance, usage patterns, and potential issues that need attention.

12 BeSpoke Customer interface(UX): The reference architecture assumes the bespoke customers centralized user interface portal will provide access to watson environment and other environments. There could be direct access to the watson services but for the purpose of this reference architecture, its assumed all via custom webportal. The access to rest of the environment can be designed as needed,as this is outside of this document design. Integration with watsonx services will be managed and monitored via customer required portal access as this enables IAM, security access credentials etc.

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

### Conversational User Experience with watsonx Assistance for Voice

Leveraging IBM's Watson Speech technology, the solution offers a sophisticated user interface that supports multiple languages, ensuring accessibility and convenience for end-users across different regions and linguistic backgrounds. The speech-to-text (STT) and text-to-speech (TTS) functionalities are hosted on IBM Cloud and consumed in this pattern.

### DevOps Pipeline

Deployment Lifecycle Management: The deployment lifecycle is managed using:

IBM Cloud Pipeline for automating development processes. IBM Cloud Registry for managing container images across different environments.

### Maximo Visual Inspection

This tool standardizes image scanning and document summarization, providing a consistent method for processing visual data within the claims process. It simplifies the extraction of relevant information from various sources, enhancing productivity and accuracy in claim handling.

Conclusion: The watsonx  solution on IBM Cloud offers an end-to-end platform tailored for financial services with a focus on AI capabilities. The architecture is designed to be scalable, secure, and highly available, ensuring that enterprises can leverage the latest advancements in AI without compromising on performance or reliability. With its comprehensive suite of tools and integration options, this solution stands ready to transform how financial institutions manage customer interactions, streamline claims processing, and maintain a vigilant watch against fraudulent activities.

This reference watsonx pattern does not describe training and finetunning of models and this is out of scope of this reference pattern.{: note}
