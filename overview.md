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

The speech and vision recognition with RAG AI pattern provides an overview and a foundation for building an enterprise artificial intelligence (AI) environment by using the watsonx architecture as the core for AI and integrating it with other {{site.data.keyword.Bluemix_notm}} services.

It combines IBM watsonx with {{site.data.keyword.Bluemix_notm}} Red Hat OpenShift, {{site.data.keyword.Bluemix_notm}} Virtual Private Cloud (VPC), Maximo Visual Inspection, and IBM Watson Voice Assistant.

It targets enterprise customers who are looking to implement an AI solution providing Retrieval Augmented Generation(RAG), speech conversation (speech to text and text to speech) and image and video analysis capabilities.

In addition, it describes how a customer can host and run x86 workloads on {{site.data.keyword.Bluemix_notm}} VPC and container workloads on {{site.data.keyword.Bluemix_notm}} Red Hat OpenShift VPC close to the watsonx environment to deliver an all in one enterprise solution.

## Industry use cases

{: usecase-id}

Review the following use case implementation across different industries for watsonx and Maximo Visual Inspection with Watson voice assistant:

1. Financial and insurance claims enhancement:
   1. Use Maximo Visual Inspection with {{site.data.keyword.Bluemix_notm}} VPC and Red Hat OpenShift to develop an insurance claim system.
   2. Analyze video feeds to detect anomalies, help in claims processing, and generate reports for approver. Help users to provide a proper search, RAG, and voice interaction with documents, images, videos.

2. Healthcare:
   1. Use watsonx to build an AI-powered application that analyzes medical images such as MRI or CT scans for disease detection and diagnosis.
   2. Integrate Maximo Visual Inspection to enable real-time image analysis and generate reports.

3. Chatbot-based customer support:
   1. Implement Watson Assistant to create a conversational interface for customer support chatbots.
   2. Provide voice and RAG implementation with documents for end customer with speech-to-text and text-to-speech.

4. Quality control for manufacturing:
   1. Use computer vision to inspect products as they move along a production line.
   2. Provide immediate feedback to manufacturing personnel, enabling them to correct issues on the spot and reduce waste.

5. Asset inspection for oil and gas:
   1. Use unmanned aerial vehicles (UAVs) or drones equipped with cameras to capture images of oil rigs, pipelines, or other assets.
   2. Employ AI-powered image analysis to detect signs of wear, damage, or malfunction in real-time.

## Considerations

{: #considerations-watson-speech}

This pattern is built on the following key technologies:

1. Watsonx: A software-as-a-service (SaaS) offering for building AI-powered applications.
2. Watson Assistant: A cloud-based AI platform for developing conversational interfaces like speech-to-text and text-to-speech.
3. watsonx.data: A managed data service that enables secure and scalable data storage.
4. watsonx.governance: A set of tools for managing and governing watson-powered AI solutions.
5. watsonx.ai: A portfolio of AI technologies, including natural language processing (NLP), machine learning (ML), and computer vision (CV).
6. {{site.data.keyword.Bluemix_notm}} VPC Red Hat OpenShift: A cloud-based infrastructure service that enables scalable and secure deployment of applications.
7. {{site.data.keyword.Bluemix_notm}} VPC VSI: A virtual server instance for running custom workloads on {{site.data.keyword.Bluemix_notm}}.
8. {{site.data.keyword.Bluemix_notm}} Development Pipelines: A continuous integration and continuous delivery (CI/CD) toolchain for automating software development workflows.
9. Code Engine as-a-Service: A cloud-based service that enables rapid application development and deployment that uses containerized applications.
10. Maximo Visual Inspection on Red Hat OpenShift Kubernetes Services on {{site.data.keyword.Bluemix_notm}} VPC : An AI-powered inspection solution for detecting defects in images and videos.

## Solution architecture

{: solution-overview}

The solution architecture is designed to address specific needs within enterprise customer who need AI RAG, with chat capability for speech and voice interaction with a bespoke client application to deal with documents ingestion and also provide image and video analysis capability for various functional and non functional requirements. This is achieved by using watsonx.ai deployed in a SaaS model. This architecture encompasses several key components that work together seamlessly to provide an end-to-end AI solution for enterprise clients. The following are the core elements of this ecosystem:

![Solution architecture](image/Overview-Pattern.svg "Solution architecture"){: caption="Figure 1. Functional overview of the watsonx AI and {{site.data.keyword.Bluemix_notm}} surround environment." caption-side="bottom"}

1. Customer data center location: A physical or virtual data center where customers can host their own infrastructure on premises. In this location, there are corporate users connecting over a secured connection on private network
2. Users: The individuals who are using applications, services, and data hosted in an {{site.data.keyword.Bluemix_notm}} environment. This includes users who will connect public network over internet.
3. Compute on {{site.data.keyword.Bluemix_notm}} through Virtual Private Cloud (VPC) and Red Hat OpenShift: Enables the deployment of traditional and containerized compute workloads while providing isolation and security for cloud-based infrastructure.
4. Watson services: A set of cognitive computing capabilities, such as natural language processing, computer vision and machine learning, which is designed to help organizations solve complex problems through AI-powered insights. Provides Retrieval Augmentation Generation (RAG) to do text retrieval and text generation and allow users to interact with documents.
5. Enhanced user experience through Watson Speech-to-Text (STT) and Text-to-Speech (TTS): Improves the way humans interact with machines by using {{site.data.keyword.IBM_notm}} Watson's Speech-to-Text (STT) and Text-to-Speech (TTS) capabilities for more natural language-based interfaces.
6. Maximo Visual Inspection: A visual inspection feature within Maximo deployed on Red Hat OpenShift Kubernetes Services on {{site.data.keyword.Bluemix_notm}} VPC, that enables users to capture and analyze video evidence of object or facility conditions, streamlining workflows and decision-making processes.
7. Application runtime services (IBM Cloud Code Engine): Offers a range of cloud-based services for deploying, managing, and optimizing application workloads in real-time, helping ensure optimal performance, scalability, and security across {{site.data.keyword.Bluemix_notm}} environments.
8. Application Life-Cycle Management (IBM Cloud Continuous Delivery): A comprehensive platform for designing, building, testing, deploying, and maintaining applications throughout their entire life cycle within an {{site.data.keyword.Bluemix_notm}} environment.
9. Storage: Provides scalable and secure cloud storage services to help customers efficiently store, manage, and retrieve large amounts of data across various types of workloads.
10. Security and compliance: Offers a suite of security solutions that are designed to protect customer data in transit and at rest, helping ensure compliance with major industry standards for confidentiality, integrity, and availability.
11. Logging and monitoring: Enables customers to collect, analyze, and visualize log data from their cloud-based applications and infrastructure, providing insights into system performance, usage patterns, and potential issues that need attention.
12. BeSpoke Customer interface (UX): The reference architecture assumes a bespoke customer centralized user interface portal provides access to the Watson environment and other environments. There might be direct access to the Watson services but for this reference architecture, it is assumed all access happens via a custom web portal. The access to the rest of the environment can be designed as needed, but this is outside of this document design.

### {{site.data.keyword.Bluemix_notm}} watsonx service

{: watsonx-service description}

IBM watsonx services on {{site.data.keyword.Bluemix_notm}} integrates with external data sources to provide a more comprehensive client experience by using RAG technology. This includes vector databases like Milvus, customer applications that are hosted on Red Hat OpenShift and watsonx.governance. watsonx.governance is a key function of the Watson offering allowing a proper administrative control over the utilization and management of watsonx.ai components.

1. Watsonx SaaS
    1. watsonx Assistant: Used for conversation flow development and web chat interface
    2. Watson Discovery: Ingest and process unstructured documents
    3. watsonx.data: Enables you to scale analytics and AI with all your data.
    4. watsonx.governance: Direct, manage and monitor the artificial intelligence activities
    5. watsonx.ai: RAG with Large Language Models (LLM) and train as needed
    6. watsonx Orchestrate: workflows and integration (Dedicated) if needed.

### Conversational user experience with watsonx Assistant for voice

{: #user-experience-overview}

Using {{site.data.keyword.IBM_notm}} Watson Speech technology, the solution offers a sophisticated user interface that supports multiple languages, helping ensure accessibility and convenience for users across different regions and linguistic backgrounds. The speech-to-text (STT) and text-to-speech (TTS) functions are hosted as services on {{site.data.keyword.Bluemix_notm}} and consumed in this pattern.

### DevOps pipeline

{: #devops-watsonx}

The deployment lifecycle is managed by using {{site.data.keyword.Bluemix_notm}} pipeline for automating development processes and {{site.data.keyword.Bluemix_notm}} registry for managing container images across different environments.

### Maximo Visual Inspection

{: #maximo-watsonx}

This tool standardizes image and video scanning and analysis, providing a consistent method for processing visual data within the claims process. It simplifies the extraction of relevant information from various sources, enhancing productivity and accuracy in claim handling.

The watsonx solution on {{site.data.keyword.Bluemix_notm}} offers an end-to-end platform that is tailored for financial services with a focus on AI capabilities. The architecture is scalable, secure, and highly available, helping ensure that enterprises can use the latest advancements in AI without compromising on performance or reliability. With its comprehensive suite of tools and integration options, this solution stands ready to transform how financial institutions manage customer interactions, streamline claims processing, and maintain a vigilant watch against fraudulent activities.

For more information, see the following links:

1. [Maximo Visual Inspection](https://www.ibm.com/docs/en/mas-cd/maximo-vi/continuous-delivery?topic=maximo-visual-inspection-edge){: external}
2. [Maximo suite overview](docs/maximo-application-suite?topic=maximo-application-suite-overview).
3. [Deployment Catalog Tile](https://cloud.ibm.com/catalog/architecture/deploy-arch-ibm-mas-fc308868-e530-4605-884e-e1b3f50b3b66-global#help){: external}

 Training and fine tuning models is considered as out of scope for this reference pattern.{: note}
