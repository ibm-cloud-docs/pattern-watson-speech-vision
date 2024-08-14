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

Watsonx is IBM's next-generation AI and data platform that is designed to help businesses build, train, deploy, and scale AI models and applications, particularly in enterprise settings. Available on IBM Cloud, Watsonx offers a suite of integrated tools and services that streamline the AI lifecycle—from data preparation to model training, deployment, and ongoing optimization.

Key Components of Watsonx on IBM Cloud:
Watsonx.ai: This is the core AI engine within Watsonx, focused on enabling AI model development and deployment. It provides pre-built, foundation models as well as tools for training custom AI models. Watsonx.ai supports both traditional machine learning models and generative AI, allowing users to build applications like chatbots, NLP-based solutions, and recommendation engines​ (IBM TechXchange Community)​ (IBM - United States).

Watsonx.data: This component is IBM's AI-optimized data store designed for scalability and governed access to both structured and unstructured data. It offers integrated data management, allowing for seamless access to data across hybrid cloud environments. Watsonx.data provides data preparation tools, governance, and connectors to a wide range of data sources, making it easy to preprocess and manage the data needed for AI/ML models​ (IBM - United States).

Watsonx.governance: This tool ensures AI systems are transparent, accountable, and trustworthy. It helps with model auditing, bias detection, explainability, and compliance tracking, making it essential for regulated industries. Watsonx.governance helps businesses ensure their AI models remain fair, unbiased, and compliant throughout their lifecycle​ (IBM TechXchange Community).

ModelOps and Lifecycle Management: Watsonx integrates with IBM’s ModelOps for continuous model monitoring, retraining, and lifecycle management. This includes deploying AI models at scale across hybrid cloud environments while providing the tools needed for ongoing monitoring and optimization​ (IBM - United States).

Hybrid and Multi-Cloud Deployment: Watsonx supports hybrid cloud and multi-cloud architectures, allowing enterprises to deploy AI models wherever they need, whether on IBM Cloud, on-premises, or across multiple cloud environments. This flexibility makes it easier to scale and adapt to enterprise requirements while maintaining control over data residency and compliance​ (IBM TechXchange Community).

## Watsonx aaS on IBM Cloud

{: #deployment-watsonx-Aas}

Customers can use the IBM Cloud watsonx-aaS service without the need to deploy any generative AI software. IBM Cloud IaaS, PaaS services provide the supporting/surround environment for a secure and regulatory compliant development and deployment of the generative AI workloads/solutions for inferencing, prompt tuning and fine tuning.

https://cloud.ibm.com/docs/watson?topic=watson-about#about

https://www.ibm.com/downloads/cas/1X7EPRYE

## Maximo Visual Inspection

The **IBM® Maximo® Visual Inspection** platform, built on cognitive infrastructure, is a new generation of video and image analysis platforms. The platform offers built-in deep learning models that learn to analyze images and video streams for classification, object detection, and anomaly detection.

![Maximo Vision.](image/architecture-image-classification-on-ibmcloud.svg "Maximo"){: caption="Figure 1. Vision RAG Pattern" caption-side="bottom"}

**Maximo Visual Inspection** includes tools and interfaces for anyone who has limited skills in deep learning technologies. You can use **IBM Maximo Visual Inspection** to label images and videos that can be used to train and validate a model. The model can then be validated and deployed in customized solutions that demand image classification, object detection, and anomaly detection.


### Integrating with Maximo Visual Inspection Edge

**Maximo Visual Inspection Edge** is a web-based application that you can integrate with **Maximo Visual Inspection** to perform AI-based inspections at the edge. You can collect images to train AI models or use trained models to inspect images from cameras that are positioned close to edge activities, such as assembly-line operations.

**Maximo Visual Inspection Edge** uses data sets and trained models that are stored in** **Maximo Visual Inspection**. In **Maximo Visual Inspection Edge**, you create inspections that process images from input sources, such as cameras or network folders. These inspections either collect images to train models or use trained models and rules to inspect images. You specify the data sets where you want to store the processed images so that models can be refined and retrained.

https://www.ibm.com/docs/en/mas-cd/maximo-vi/continuous-delivery?topic=maximo-visual-inspection-edge

![Visual Inspection for image and Video.](image/video-ingestion.drawio.svg "Image and Video analysis"){: caption="Figure 1. Video and images  RAG Pattern" caption-side="bottom"}

## Watson Speech:

**IBM Cloud Speech to Text service**

![Watson Speech.](image/speech-to-text-transcription-pipeline.svg "Watson Speech"){: caption="Figure 1. Speech to Text transcription pipeline" caption-side="bottom"}

IBM Cloud Speech to Text service converts the human voice into the written word. The service uses deep-learning artificial intelligence to apply knowledge of grammar, language structure, and the composition of audio and voice signals to accurately transcribe human speech. It can be used in applications such as voice-automated chatbots, analytic tools for customer-service call centers, and multi-media transcription, among many others.

The service is available in multiple languages.


**IBM Cloud Text to Speech service**

IBM Cloud Text to Speech service converts written text to natural-sounding speech. The service streams the synthesized audio back with minimal delay. The audio uses appropriate cadence and intonation for its language and dialect to provide voices that are smooth and natural. The service can be used in applications such as voice-automated chatbots, as well as a variety of voice-driven and screenless applications, such as tools for the disabled or visually impaired, video narration and voice over, and educational and home-automation solutions.


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
