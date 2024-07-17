---
copyright:
  years: 2024
lastupdated: "2024-03-26"

subcollection: watsonx

keywords:
---
{{site.data.keyword.attribute-definition-list}}

# Overview

{: #overview-id}

## Overview of the overall solution

watsonx on IBM Cloud addressing enterprise clients AI requirements

In this use case we follow the specifics for watsonx ai covering Financial Services sector.

This reference architectcure coveres financial services use case which has the following requirements

1. watsonx AI deployment on Cloud.(SaaS)
2. Chatbot for end user and internal user to chat with documents.(SaaS)
3. end user chat using web for speech to text and text to speech for communication.**( STT and TTS)**
4. end user chatbot for general query using RAG with documents.(SaaS)
5. ability to process and summarise claims for faster claims process via generative watsonx.(RAG integrate with images/Video and walk to Speech and Text)
6. ability to recognise images and video for claims and process purpose.( maximo visual I) high level, but will provide all guidance to navigate to desired outcome.
7. integration with the clients relational database to ibntegrated with RAG/CRAG.
8. ability to intergate and host x86 and container workload across HA environment/ DR optinal ( itnegrate with watsonx).
9. IBM Cloud hosting fulfillment requirement(vector, storage,monitoring)

### Detailed explaination:

1.Chatbots
and Virtual Assistants: Build conversational watsonai models for legal and
insurance applications to provide customer support, automate repetitive tasks,
and extract relevant information from user inputs.

2.Use of watson speech withassistance to provide better user experience.

3.Claims
Processing and Fraud Detection: Use Maximo visual inspection to  automate claims processing, extract key
information from claim forms using image scanning and video scanning to detect
fraudulent claims using anomaly detection algorithms and predictive models.
This can save time, reduce errors, and improve customer satisfaction.

4.Utilise the application development on VPC and ROKS platform.

5.Retrieval-augmented generation with external data sources for better client experience.

Technical details covered in these sections are as follows.

•Deployed across IBM Cloud  Multi Region( no DR)

•Consume watsonx service from IBM Cloud/Optional to have dedicated as second reference.

•Guidance on IBM watsonx deployment options as simple, medium, large production deployment based on following
requirements.

**Watson**

•Standard watson deployment solution components.

•watsonx Assistant – Used to conversation flow development and webchat interface

•watson Discovery – Used to ingest documents that will be used to retrieve relevant docs.

•watsonx ai – RAG with LLM on VPC.

•*watson orchestrate- workflows and integration(Dedicated)

•IBM Cloud Surround recommended repeatable components

•ROKS/VM( single and Multi ZR)

•App development.

• Vector DB for RAG

•ICD.

•PostgreSQL on IBM Cloud.

•Milvus Vector DB hosted on ROKS integrate with RAG.

•Storage:

•IBM COS (Cloud Object Storage) for storage.

•Block Storage.

•File Storage Aspera addition

•Logging / Monitoring:

•IBM Cloud Activity Tracker

•IBM Cloud Logs.

•Code Engine:

•Lifecycle / Deployment:

•Use IBM Cloud Pipeline for development and Cloud Registry.

•Maximo Visual inspection: Standard Maas for image scanning and summarization.

•Speech watson

•Speech to text and Text to speech with multi language support on  VPC GPU. Speech summarization for users and
virtual ai conversation.

•STT

•TTS

•Aspera or general means to upload mp3 files.
