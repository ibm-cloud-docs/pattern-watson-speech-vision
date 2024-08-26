---
copyright:
  years: 2024
lastupdated: "2024-08-26"

subcollection: watsonx

keywords:
---

{{site.data.keyword.attribute-definition-list}}

# Overview
{: overview-watsonx-speech}

The watsonx integration with speech and vision pattern provides an overview and a foundation for building an enterprise artificial intelligence (AI) environment by using the watsonx architecture as the core for AI and integration with other {{site.data.keyword.Bluemix_notm}} services. It combines watsonx with {{site.data.keyword.Bluemix_notm}} Red Hat OpenShift, Virtual Private Cloud (VPC), Maximo Visual Inspection, and Watson Voice Assistance to deliver AI solutions that meets Retrieval Augmentation Generation (RAG), real-time analytics, speech recognition, image, and video detection. This pattern is helpful for the enterprise customers in focusing on AI that needs to delivery RAG, speech, and image and video detection. In addition, it describes how a customer can host and run x86 on {{site.data.keyword.Bluemix_notm}} VPC and container workloads on {{site.data.keyword.Bluemix_notm}} Red Hat OpenShift VPC close to watsonx environment delivery all in one enterprise solution.

## Industry use cases
{: usecase-id}

Review the following use case implementation across different industries for watsonx and Maximo Visual Inspection with Watson voice assistance:

1. Financial and insurance claims enhancement: 
   1. Use Maximo Visual Inspection with {{site.data.keyword.Bluemix_notm}} VPC Red Hat OpenShift to develop an insurance claim system. 
   2. Analyze video feeds to detect anomalies, help in claims processing, and generate reports for approver. Help users to provide a proper search, RAG, and voice interaction with documents, images, videos.

2. Healthcare:
   1. Use watsonx to build an AI-powered application that analyzes medical images such as MRI's or CT scans for disease detection and diagnosis. 
   2. Integrate Maximo Visual Inspection to enable real-time image analysis and generate reports.
   3. Use cameras that are installed on medical equipment like MRI machines or in storage areas to capture images of devices.
   4. Apply computer vision algorithms to analyze the images and detect signs of wear, damage, or malfunction in real-time.
   5. Integrate with RAG and voice to provide a better user experience.
   
3. Chatbot-based customer support: 
   1. Implement Watson Assistant to create a conversational interface for customer support chatbots.
   2. Provide voice and RAG implementation with documents for end customer with speech-to-text and text-to-speech.

4. Quality control for manufacturing:
   1. Use computer vision to inspect products as they move along a production line.
   2. Detect defects or irregularities in real-time using AI-powered image analysis.
   3. Provide immediate feedback to manufacturing personnel, enabling them to correct issues on the spot and reduce waste.
   4. Integrate with RAG and voice to provide a better user experience.

5. Asset inspection for oil and gas:
   1. Use unmanned aerial vehicles (UAVs) or drones equipped with cameras to capture images of oil rigs, pipelines, or other assets.
   2. Employ AI-powered image analysis to detect signs of wear, damage, or malfunction in real-time.
   3. Integrate with RAG and voice to provide a better user experience.

## Considerations
{: #considerations-watson-speech}

This pattern is built on the following key technologies:

1. Watsonx: A software-as-a-service (SaaS) offering for building AI-powered applications.
2. Watson Assistant: A cloud-based AI platform for developing conversational interfaces like speech-to-text and text-to-speech.
3. watson.data: A managed data service that enables secure and scalable data storage.
4. watson.governance: A set of tools for managing and governing watson-powered AI solutions.
5. watson.ai: A portfolio of AI technologies, including natural language processing (NLP), machine learning (ML), and computer vision (CV).
6. {{site.data.keyword.Bluemix_notm}} VPC Red Hat OpenShift: A cloud-based infrastructure service that enables scalable and secure deployment of applications.
7. {{site.data.keyword.Bluemix_notm}} VPC VSI: A virtual server instance for running custom workloads on {{site.data.keyword.Bluemix_notm}}.
8. {{site.data.keyword.Bluemix_notm}} Development Pipelines: A continuous integration and continuous delivery (CI/CD) toolchain for automating software development workflows.
9. Code Engine as-a-Service: A cloud-based service that enables rapid application development and deployment that uses containerized applications.
10. Maximo Visual Inspection on ROKS VPC : An AI-powered inspection solution for detecting defects in images and videos.

## Solution architecture
{: solution-overview}

The solution architecture is designed to address specific needs within enterprise customer who need AI RAG, with Chat capability for speech and voice interaction with the bespoke client application to deal with documents ingestion and also provide ability for image and video recognition for various functional and nonfunctional requirements. This is achieved by watsonx AI deployment in a SaaS model. This architecture encompasses several key components that work together seamlessly to provide an end-to-end AI solution for enterprise clients. The following are the core elements of this ecosystem:

![Solution architecture](image/Overview-Pattern.svg){: caption="Figure 1. Functional overview of the watsonx AI and {{site.data.keyword.Bluemix_notm}} surround environment." caption-side="bottom"}

1. Customer data center location: A physical or virtual data center where customers can host their own infrastructure on {{site.data.keyword.Bluemix_notm}}.
1. Users: The individuals who are using applications, services, and data hosted in an {{site.data.keyword.Bluemix_notm}} environment.
1. Compute on {{site.data.keyword.Bluemix_notm}} through Virtual Private Cloud (VPC) Red Hat OpenShift: Enables the deployment of compute workloads into a Virtual Private Cloud (VPC) or Red Hat OpenShift, providing isolation and security for cloud-based infrastructure. 
1. Watson services: A set of cognitive computing capabilities, such as natural language processing, computer vision, and machine learning, which is designed to help organizations solve complex problems through AI-powered insights. Provides Retrieval Augmentation Generation (RAG) to do text retrieval and text generation allowing users to interact with documents.
1. Enhanced user experience through Watson Speech-to-Text (STT) and Text-to-Speech (TTS): Improves the way humans interact with machines by using {{site.data.keyword.IBM_notm}} Watson's Speech-to-Text (STT) and Text-to-Speech (TTS) capabilities for more natural language-based interfaces.
1. Maximo Visual Inspection: A visual inspection feature within Maximo, an asset management platform, that enables users to capture and analyze video evidence of equipment or facility conditions, streamlining maintenance workflows and decision-making processes.
1. Application runtime services: Offers a range of cloud-based services for deploying, managing, and optimizing application workloads in real-time, helping ensure optimal performance, scalability, and security across {{site.data.keyword.Bluemix_notm}} environments.
1. Apps Life-Cycle Management: A comprehensive platform for designing, building, testing, deploying, and maintaining applications throughout their entire life cycle within an {{site.data.keyword.Bluemix_notm}} environment.
1. Storage: Provides scalable and secure cloud storage services to help customers efficiently store, manage, and retrieve large amounts of data across various types of workloads.
1. Security and compliance: Offers a suite of security solutions that are designed to protect customer data in transit and at rest, helping ensure compliance with major industry standards for confidentiality, integrity, and availability.
1. Logging and monitoring: Enables customers to collect, analyze, and visualize log data from their cloud-based applications and infrastructure, providing insights into system performance, usage patterns, and potential issues that need attention.
1. BeSpoke Customer interface (UX): The reference architecture assumes the bespoke customers centralized user interface portal provides access to the Watson environment and other environments. There might be direct access to the Watson services but for this reference architecture, it's is assumed all via custom web portal. The access to the rest of the environment can be designed as needed, as this is outside of this document design. Integration with watsonx services is managed and monitored by the customer-required portal access as this enables IAM, security access credentials, and so on.

### {{site.data.keyword.Bluemix_notm}} watsonx service
{: watsonx-service description}

The watsonx as a service on {{site.data.keyword.Bluemix_notm}} integrates with external data sources to provide a more comprehensive client experience by using RAG technology for retrieving relevant documents and information from vast datasets. This includes vector databases like Milvus and customer apps that are hosted on ROKS.governance, which is a key functions of the Watson offering allowing a proper administrative control over the utilization and management of watsonx AI components.

1.  Watsonx SaaS
    1. Watson Assistant: Used for conversation flow development and web chat interface Watson Discovery – Used to ingest documents that will be used to retrieve relevant docs. 
    2. Watson Data
    3. Watson Governance
    4. Watson AI: RAG with LLM and train as needed. 
    5. Watson orchestrate: workflows and integration (Dedicated) if needed.

### Conversational user experience with watsonx Assistance for voice
{: user-experience-overview}

Using {{site.data.keyword.IBM_notm}} Watson Speech technology, the solution offers a sophisticated user interface that supports multiple languages, helping ensure accessibility and convenience for users across different regions and linguistic backgrounds. The speech-to-text (STT) and text-to-speech (TTS) functions are hosted on {{site.data.keyword.Bluemix_notm}} and consumed in this pattern.

### DevOps pipeline
{# devops-watsonx}

The deployment lifecycle is managed by using {{site.data.keyword.Bluemix_notm}} pipeline for automating development processes and {{site.data.keyword.Bluemix_notm}} registry for managing container images across different environments.

### Maximo Visual Inspection
{: #maximo-watsonx}

This tool standardizes image scanning and document summarization, providing a consistent method for processing visual data within the claims process. It simplifies the extraction of relevant information from various sources, enhancing productivity and accuracy in claim handling.

The watsonx solution on {{site.data.keyword.Bluemix_notm}} offers an end-to-end platform that is tailored for financial services with a focus on AI capabilities. The architecture is scalable, secure, and highly available, helping ensure that enterprises can use the latest advancements in AI without compromising on performance or reliability. With its comprehensive suite of tools and integration options, this solution stands ready to transform how financial institutions manage customer interactions, streamline claims processing, and maintain a vigilant watch against fraudulent activities.

This reference watsonx pattern does not describe training and fine-tuning of models and this is out of the scope of this reference pattern.
{: note}
