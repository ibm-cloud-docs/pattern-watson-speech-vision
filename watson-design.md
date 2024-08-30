---
copyright:
  years: 2024
lastupdated: [2024-08-30]

subcollection: pattern-watson-speech-vision

keywords:
---
{{site.data.keyword.attribute-definition-list}}

# Watsonx design considerations
{: #ai-products-watsonx}

The following are the Artificial Intelligence design considerations for the the speech and vision recognition with RAG AI pattern pattern, covering conversational speech to text and text to speech and computer vision.

## Requirements
{: #ai-products-watsonx-requirements}

The Watson pattern AI solution requires a range of AI components to effectively process and analyze various types of data inputs. These requirements are designed to meet specific business needs, including Retrieval-Augmented Generation (RAG), Chat (voice and text interaction), image detection, and video detection.

1. Retrieval Augmentation Generation (RAG): The AI system must be able to do text retrieval and text generation.
2. Voice and text chat: The AI system should support voice and text interaction through various channels, such as:
   1. Speech to text conversion: Converting spoken words into written text for processing and analysis.
   2. Text to speech conversation: The AI system must be able to process and analyze large volumes of textual data from various sources including image detection.
3. Image Detection: The AI system should include computer vision capabilities for analyzing images, such as:
   1. Object detection: Recognizing specific objects within an image.
   2. Image classification: Categorizing images based on their content or context.
4. Video Detection: The AI system must be able to process and analyze nonlive video data that's uploaded into from various sources, including:
   1. Object tracking: Following the movement of specific objects over time in a video sequence.
   2. Video analysis: Detecting patterns, trends, or anomalies within a video.

## IBM watsonx Services on IBM Cloud
{: #watsonx-services}

Watsonx is IBM's next-generation AI and data platform that is designed to help businesses build, train, deploy, and scale AI models and applications, particularly in enterprise settings. Available on {{site.data.keyword.Bluemix_notm}}, watsonx offers a suite of integrated tools and services that streamline the AI lifecycle—from data preparation to model training, deployment, and ongoing optimization.

Key Components of watsonx on {{site.data.keyword.Bluemix_notm}}:

1. watsonx.ai: This is the core AI engine within watsonx, focused on enabling AI model development and deployment. It provides pre-built, foundation models as well as tools for training custom AI models.
2. watsonx.data: This component is IBM's AI-optimized data store designed for scalability and governed access to both structured and unstructured data.
3. watsonx.governance: This tool helps ensure AI systems are transparent, accountable, and trustworthy. It helps with model auditing, bias detection, explainability, and compliance tracking, making it essential for regulated industries.
4. IBM watsonx Assistant for Voice: Conversational capabilities for speech and text.

For more information, see [Getting started with Watson and IBM Cloud](/docs/watson?topic=watson-about#about).
{: note}

## Maximo Visual Inspection
{: #maximo-inspection}

The {{site.data.keyword.IBM_notm}} Maximo Visual Inspection platform that's built on cognitive infrastructure is a new generation of video and image analysis platforms. The platform offers built-in deep learning models that learn to analyze images and video streams for classification, object detection, and anomaly detection.

![Visual Inspection for image and Video.](image/functional-flows-architecture-image-classification-on-ibmcloud.svg "Image and Video analysis"){: caption="Figure 1. Video and images watsonx pattern" caption-side="bottom"}

Maximo Visual Inspection includes tools and interfaces for anyone with limited skills in deep learning technologies. You can use {{site.data.keyword.IBM_notm}}. Maximo Visual Inspection can be customized and deployed that demand image classification, object detection, and anomaly detection.

Maximo Visual Inspection Edge is a web-based application that you can integrate with Maximo Visual Inspection to perform AI-based inspections at the edge. Maximo Visual Inspection Edge uses data sets and trained models that are stored in Maximo Visual Inspection. In Maximo Visual Inspection Edge, you create inspections that process images from input sources.

For more information, see the following links:

1. [Maximo Visual Inspection](https://www.ibm.com/docs/en/mas-cd/maximo-vi/continuous-delivery?topic=maximo-visual-inspection-edge){: external}.
2. [Maximo suite overview](/docs/maximo-application-suite?topic=maximo-application-suite-overview).
3. [Deployment catalog Tile](https://cloud.ibm.com/catalog/architecture/deploy-arch-ibm-mas-fc308868-e530-4605-884e-e1b3f50b3b66-global#help){: external}.

This reference pattern does not describe training and fine-tuning of models, that's out of scope for this reference pattern.{: note}

## IBM watsonx Assistant for Voice
{: #watsonx-assistant-voice}

{{site.data.keyword.IBM_notm}} watsonx Assistant for Voice offers:

1. Advanced artificial intelligence technology that blends large speech models (LSMs) voice recognition, speech to text, and NLU capabilities.
2. Expressive voices designed to respond to customer requests in natural human-like speech with ability to understand expressions and analyze conversation sentiment. For more information, see [watsonx Assistant for Voice](https://www.ibm.com/products/watsonx-assistant/voice){: external} and [watsonx Assistant](/docs/watson-assistant?topic=watson-assistant-welcome-new-assistant).

### Speech to Text service
{: #speech-text-service}

{{site.data.keyword.Bluemix_notm}} Speech to Text service converts the human voice into the written word. The service uses deep-learning artificial intelligence to apply knowledge of grammar, language structure, and the composition of audio and voice signals to accurately transcribe human speech. It can be used in applications such as voice-automated chatbots, analytic tools for customer-service call centers, and multi-media transcription, among many others.

![Watson Speech](image/functional-flows-speech-to-text-transcription-pipeline-with-labels.svg "Watson Speech"){: caption="Figure 2. Speech to Text transcription pipeline" caption-side="bottom"}

The service is available in multiple languages and is exposed as an 'http' interface and a WebSocket interface. It can be accessed by using a public or a private endpoint. For more information, see [Getting started with Watson Speech to Text](/docs/speech-to-text?topic=speech-to-text-gettingStarted).

### Text to Speech service
{: #text-to-speech}

{{site.data.keyword.Bluemix_notm}} Text to Speech service converts written text to natural-sounding speech. The service streams the synthesized audio back with minimal delay. The audio uses appropriate cadence and intonation for its language and dialect to provide voices that are smooth and natural.

The service is exposed as an http interface (synchronous and asynchronous) and a WebSocket interface. It can be accessed by using a public or a private endpoint. Please refer to reference section for additional reference links to the service.
