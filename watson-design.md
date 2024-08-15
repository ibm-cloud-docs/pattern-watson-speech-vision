---
copyright:
  years: 2024
lastupdated: "2024-03-29"

subcollection: pattern-watson-speech-vision

keywords:
---
{{site.data.keyword.attribute-definition-list}}

# Watsonx design considerations

{: #ai-products-watsonx}

## Requirement

The Watson Pattern AI solution requires a range of AI components to effectively process and analyze various types of data inputs. These requirements are designed to meet specific business needs, including RAG, Chat (Voice, Text Interaction), Image Detection and Video Detection.

1. Retrieval Augmentation Generation (RAG) : The AI system must be able to do Text Retrieval and Text Generation
2. Voice and text chat : The AI system should support voice and text interaction through various channels, such as:

   1. Speech-to-text conversion: converting spoken words into written text for processing and analysis
   2. Text to Speech conversation : The AI system must be able to process and analyze large volumes of textual data from various sources, including
3. Image Detection : The AI system should include computer vision capabilities for analyzing images, such as:

   1. Object detection: recognizing specific objects within an image
   2. Image classification: categorizing images based on their content or context
4. Video Detection : The AI system must be able to process and analyze video( Non Live)) data uploaded into from various sources, including:

   1. Object tracking: following the movement of specific objects over time in a video sequence.
   2. Video analysis: detecting patterns, trends, or anomalies within a video

## Watson x SaaS model components

Watsonx is IBM's next-generation AI and data platform that is designed to help businesses build, train, deploy, and scale AI models and applications, particularly in enterprise settings. Available on IBM Cloud, Watsonx offers a suite of integrated tools and services that streamline the AI lifecycle—from data preparation to model training, deployment, and ongoing optimization.

Key Components of Watsonx on IBM Cloud:

1. Watsonx.ai:This is the core AI engine within Watsonx, focused on enabling AI model development and deployment. It provides pre-built, foundation models as well as tools for training custom AI models.
2. Watsonx.data: This component is IBM's AI-optimized data store designed for scalability and governed access to both structured and unstructured data. It offers integrated data management, allowing for seamless access to data across hybrid cloud environments. Watsonx.data provides data preparation tools, governance, and connectors to a wide range of data sources.
3. Watsonx.governance: This tool ensures AI systems are transparent, accountable, and trustworthy. It helps with model auditing, bias detection, explainability, and compliance tracking, making it essential for regulated industries. Watsonx.governance helps businesses ensure their AI models remain fair, unbiased, and compliant throughout their lifecycle.
4. IBM watsonx Assistant for Voice:

https://cloud.ibm.com/docs/watson?topic=watson-about#about

https://www.ibm.com/downloads/cas/1X7EPRYE

## Maximo Visual Inspection(Siva to modify the image)

The **IBM® Maximo® Visual Inspection** platform, built on cognitive infrastructure, is a new generation of video and image analysis platforms. The platform offers built-in deep learning models that learn to analyze images and video streams for classification, object detection, and anomaly detection.

![Maximo Vision.](image/architecture-image-classification-on-ibmcloud.svg "Maximo"){: caption="Figure 1. Vision RAG Pattern" caption-side="bottom"}

Maximo Visual Inspection includes tools and interfaces for anyone who has limited skills in deep learning technologies. You can use IBM Maximo Visual Inspection to label images and videos that can be used to train and validate a model. The model can then be validated and deployed in customized solutions that demand image classification, object detection, and anomaly detection.

### Integrating with Maximo Visual Inspection Edge( remove the diagram and use as contest from Siva diagram)

**Maximo Visual Inspection Edge** is a web-based application that you can integrate with **Maximo Visual Inspection** to perform AI-based inspections at the edge. You can collect images to train AI models or use trained models to inspect images from cameras that are positioned close to edge activities, such as assembly-line operations.

**Maximo Visual Inspection Edge** uses data sets and trained models that are stored in** **Maximo Visual Inspection**. In **Maximo Visual Inspection Edge**, you create inspections that process images from input sources, such as cameras or network folders. These inspections either collect images to train models or use trained models and rules to inspect images. You specify the data sets where you want to store the processed images so that models can be refined and retrained.

https://www.ibm.com/docs/en/mas-cd/maximo-vi/continuous-delivery?topic=maximo-visual-inspection-edge

![Visual Inspection for image and Video.](image/video-ingestion.drawio.svg "Image and Video analysis"){: caption="Figure 1. Video and images  RAG Pattern" caption-side="bottom"}

## watsonx Assistant for Voice( Siva)

IBM watsonx Assistant for Voice offers:

1. Advanced artificial intelligence technology that blends large speech models (LSMs) voice recognition, speech to text, and NLU capabilities.
2. Expressive voices designed to respond to customer requests in natural human-like speech with ability to understand expressions and analyze conversation sentiment.
3. Analytics that reveal valuable insights like popular customer queries, FAQs, emerging topics, user experience feedback, and satisfaction levels, empowering you to create personalized interactions.
4. More information https://www.ibm.com/products/watsonx-assistant/voice
5. additional information https://cloud.ibm.com/docs/watson-assistant?topic=watson-assistant-welcome-new-assistant

**IBM Cloud Speech to Text service**

![Watson Speech.](image/speech-to-text-transcription-pipeline.svg "Watson Speech"){: caption="Figure 1. Speech to Text transcription pipeline" caption-side="bottom"}

IBM Cloud Speech to Text service converts the human voice into the written word. The service uses deep-learning artificial intelligence to apply knowledge of grammar, language structure, and the composition of audio and voice signals to accurately transcribe human speech. It can be used in applications such as voice-automated chatbots, analytic tools for customer-service call centers, and multi-media transcription, among many others.

The service is available in multiple languages and is exposed as an http interface and a websocket interface. It can be accessed using a public or a private endpoint.

https://cloud.ibm.com/docs/speech-to-text?topic=speech-to-text-gettingStarted

**IBM Cloud Text to Speech service**

IBM Cloud Text to Speech service converts written text to natural-sounding speech. The service streams the synthesized audio back with minimal delay. The audio uses appropriate cadence and intonation for its language and dialect to provide voices that are smooth and natural. The service can be used in applications such as voice-automated chatbots, as well as a variety of voice-driven and screenless applications, such as tools for the disabled or visually impaired, video narration and voice over, and educational and home-automation solutions.

The service is exposed as an http interface (synchronous and asynchronous) and a websocket interface. It can be accessed using a public or a private endpoint.

## Reference

1. https://cloud.ibm.com/docs/watson-assistant?topic=watson-assistant-welcome-new-assistant
2. https://www.ibm.com/products/watson-discovery/use-cases
3. https://www.ibm.com/products/watsonx-ai
4. https://www.ibm.com/products/watsonx-data
5. https://www.ibm.com/products/watsonx-governance
6. https://www.ibm.com/docs/en/mas-cd/maximo-vi/continuous-delivery?topic=planning-supported-gpus-devices
7. https://www.ibm.com/docs/en/mas-cd/maximo-vi/continuous-delivery?topic=overview
8. https://www.ibm.com/docs/en/mas-cd/maximo-vi/continuous-delivery?topic=configuring.
9. https://www.ibm.com/docs/en/mas-cd/maximo-vi/continuous-delivery?topic=maximo-visual-inspection-edge.
10. https://www.ibm.com/products/maximo/pricing#price-estimator
11. https://cloud.ibm.com/docs/text-to-speech?topic=text-to-speech-gettingStarted
12. https://cloud.ibm.com/docs/text-to-speech?topic=text-to-speech-speech-install-data
13. https://cloud.ibm.com/docs/speech-to-text?topic=speech-to-text-speech-install-data
14. https://cloud.ibm.com/docs/openwhisk?topic=openwhisk-pkg_text_to_speech
15. https://cloud.ibm.com/docs/text-to-speech?topic=text-to-speech-gettingStarted
16. https://cloud.ibm.com/docs/speech-to-text?topic=speech-to-text-gettingStarted
17. https://cloud.ibm.com/docs/speech-to-text
18. https://dataplatform.cloud.ibm.com/docs/content/svc-welcome/wstt.html?context=cpdaas
