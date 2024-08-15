---
copyright:
  years: 2024
lastupdated: "2024-03-29"

subcollection: pattern-watson-speech-vision

keywords:
---

{{site.data.keyword.attribute-definition-list}}

# Watsonx Architecture decision (dwarka)

{: \#ai-products-watsonx}

## Architecture decisions for Watson AI

Watsonx is IBM’s AI and data platform with three core components and a set of AI assistants designed to help to scale and accelerate the impact of AI with trusted data across businesses.

Core components include watsonx.ai, watsonx.data and watsonx.governance.

Watsonx.ai - a studio for new foundation models, generative AI and machine learning; : It comprises of Watson Studio and Watson Machine Learning services that are extended with features for working with foundation models and generative AI.

Watsonx.data - a fit-for-purpose data store built on an open data lakehouse architecture; : It comprises of a single unified data platform based on open lakehouse architecture, open data formats and opensource Presto engine for querying.

Watsonx.governance - a toolkit, to accelerate AI workflows that are built with responsibility, transparency and explainability. : It comprises of Open Scale, AI Factsheets and Open Pages services that are integrated and enhanced with features for working with foundation models and generative AI. Services will be rebranded with current focus on integrating and Open Scale, AI Factsheets with Open Pages integration to follow.

| **Architecture decision**                                  | **Requirement**                                                                                                                            | **Alternative**                           | **Decision**        | **Rationale**                                                                                                                                                                                                                                                                                                                                                                                  |
|------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------|---------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Chat assistance                                            | Create customer user chatbot that can integrate with AI and provide speech text interaction.                                               | Provide external opensource or 3rd Party. | watsonx Assistant   | Designed to create exceptional customer service experiences, watsonx Assistant empowers everyone in the organization to build and deploy AI-powered virtual agents without writing a line of code.                                                                                                                                                                                             |
| Generative ai framework with LLM and external data sources | Create a Generative AI solution that can work with documents and provide better user experience. Integrates with the customer data sources | 3rd party MS Co-pilot                     | Watsonx.ai          | a studio for new foundation models, generative AI and machine learning; : It comprises of Watson Studio and Watson Machine Learning services that are extended with features for working with foundation models and generative AI.                                                                                                                                                             |
| **AI database.**                                           | **Provide database for Generative AI**                                                                                                     |                                           | **Watsonx.data**    | **a fit-for-purpose data store built on db2 architecture; : It comprises of a single unified data platform based on DB2 architecture.**                                                                                                                                                                                                                                                        |
| ai governance                                              | Provide governance                                                                                                                         | NONE.                                     | Watsonx. Governance | a toolkit, to accelerate AI workflows that are built with responsibility, transparency and explainability. : It comprises of Open Scale, AI Factsheets and Open Pages services that are integrated and enhanced with features for working with foundation models and generative AI. Services will be rebranded with current focus on integrating and Open Scale, AI Factsheets with Open Pages |
