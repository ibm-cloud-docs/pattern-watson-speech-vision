---
copyright:
  years: 2024
lastupdated: "2024-08-28"

subcollection: pattern-watson-speech-vision

keywords:
---
{{site.data.keyword.attribute-definition-list}}

# Watsonx architecture decision
{: #ai-products-watsonx-decisions}

## Architecture decisions for Watson AI
{: #ai-products-watsonx-architecture}

{{site.data.keyword.IBM_notm}} watsonx is {{site.data.keyword.IBM_notm}}'s AI and data platform with three core components and a set of AI assistants that are designed to help to scale and accelerate the impact of AI with trusted data across businesses.

The following are the core components include watsonx.ai, watsonx.data, and watsonx.governance:

* watsonx.ai: A studio for new foundation models, generative AI, and machine learning. It consists of Watson Studio and Watson Machine Learning services that are extended with features for working with foundation models and generative AI.
* watsonx.data: A fit-for-purpose data stores built on an open data lakehouse architecture. It consists of a single unified data platform based on open lakehouse architecture, open data formats, and an open sourced Presto engine for querying.
* watsonx.governance: A toolkit, to accelerate AI workflows that are built with responsibility, transparency, and explainability. It consists of Open Scale, AI Factsheets, and Open Pages services that are integrated and enhanced with features for working with foundation models and generative AI. Services are rebranded with current focus on integrating and Open Scale, AI Factsheets with Open Pages integration to follow.

| Architecture decision                            | Requirement                                                                                                                      | Alternative                                                               | Decision  | Rationale                                                                                                                                                                                                                                                                                                                                                                                                 |
| ---------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------- | ------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Chat assistance                                            | Create a customer user chatbot that can integrate with AI and provide speech and text interaction.                                               | Provide external open source or 3rd Party.                                           | watsonx Assistant   | Designed to create exceptional customer service experiences, watsonx Assistant empowers everyone in the organization to build and deploy AI-powered virtual agents without writing a line of code.                                                                                                                                                                                                                  |
| Generative AI framework with Large Language Model (LLM) and external data sources | Create a Generative AI solution that can work with documents and provide a better user experience. It integrates with the customer data sources. | Microsoft Copilot with Third-Party Applications                                              | watsonx.ai          | A studio for new foundation models, generative AI, and machine learning. It's comprised of Watson Studio and Watson Machine Learning services that are extended with features for working with foundation models and generative AI.                                                                                                                                                                                  |
| Watson AI database                                      | Provide database for Generative AI                                                                                                         | {{site.data.keyword.IBM_notm}} watsonx.data Milvus \n {{site.data.keyword.IBM_notm}} watsonx.data Presto \n Chroma database \n Pine Cone | watsonx.data Milvus | Milvus is a vector database that stores, indexes, and manages massive embedding vectors that are developed by deep neural networks and other machine learning (ML) models. It is developed to empower embedding similarity search and AI applications. Milvus makes unstructured data search more accessible and consistent across various environments.                                      |
| AI governance                                              | Provide governance                                                                                                                         | 3rd Party Governance opensource                                                     | watsonx.Governance | Centralized governance to manage and monitor AI workflows that are built with responsibility, transparency and explainability.  It's comprised of Open Scale, AI Factsheets, and Open Pages services that are integrated and enhanced with features for working with foundation models and generative AI. Services will be rebranded with current focus on integrating and Open Scale and AI Factsheets with Open Pages. |
