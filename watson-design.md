---
copyright:
  years: 2024
lastupdated: "2024-03-29"

subcollection: pattern-watson-speech-vision

keywords:
---
{{site.data.keyword.attribute-definition-list}}

## Watsonx

{: #ai-products-watsonx}

Watsonx is IBM’s AI and data platform with three core components and a set of AI assistants designed to help to scale and accelerate the impact of AI with trusted data across businesses.

Core components include watsonx.ai, watsonx.data and watsonx.governance.

Watsonx.ai - a studio for new foundation models, generative AI and machine learning; : It comprises of Watson Studio and Watson Machine Learning services that are extended with features for working with foundation models and generative AI.

Watsonx.data - a fit-for-purpose data store built on an open data lakehouse architecture; : It comprises of a single unified data platform based on open lakehouse architecture, open data formats and opensource Presto engine for querying.

Watsonx.governance - a toolkit, to accelerate AI workflows that are built with responsibility, transparency and explainability. : It comprises of Open Scale, AI Factsheets and Open Pages services that are integrated and enhanced with features for working with foundation models and generative AI. Services will be rebranded with current focus on integrating and Open Scale, AI Factsheets with Open Pages integration to follow.

AI assistants are pre-built applications powered by watsonx. They enable automating customer service, generating code, and automating key workflows in departments such as HR.

* watsonx Assistant: Designed to create exceptional customer service experiences, watsonx Assistant empowers everyone in the organization to build and deploy AI-powered virtual agents without writing a line of code.
* watsonx Orchestrate: With an expanding catalog of capabilities, business users can use watsonx Orchestrate to delegate common and complex talent management tasks such as creating a job description, pulling a report in Salesforce or SAP SuccessFactors, sourcing candidates and more using natural language.
* watsonx Code Assistant: Empower developers of all experience levels to write code with AI-generated recommendations. Purpose-built for targeted use cases such as application modernization and IT automation, watsonx Code Assistant leverages generative AI to increase developer productivity, reduce coding complexity, and accelerate developer onboarding.
* Watsonx Orders: AI-powered voice agent that accurately takes orders from your drive-thru guests and speeds them to the pay window. It supports a multitude of use cases, including loyalty programs and mobile orders. It knows the customization options of every menu item. It’s aware of what’s available and what’s not. And it works every shift, every day.

## Types of Gen AI workloads

{: #concepts-types-gen-ai-workloads}

Generative AI workloads typically fall into these following categories:

* Inferencing: The process of using a trained machine learning model to make predictions on new data.
* Prompt Tuning: An efficient, low-cost way of adapting a pre-trained model to new tasks without retraining the model or updating its weights. Prompt tuning involves learning a small number of new parameters that are appended to a model’s prompt, while freezing the model’s existing parameters.
* Fine Tuning: The process of adapting a pre-trained model to perform a specific task by conducting additional training. Fine tuning may involve (1) updating the model’s existing parameters, known as full fine tuning, or (2) updating a subset of the model’s existing parameters or adding new parameters to the model and training them while freezing the model’s existing parameters, known as parameter-efficient fine tuning.
* Model Training: The initial stage of model building, involving a subset of the source data. The model learns by example from the known data. The model can then be tested against a further, different subset for which the outcome is already known.

Given the current state of technology, we think that most IBM Cloud clients will be focusing on using/creating solutions that involve Inferencing, Prompt Tuning and Fine Tuning. A much smaller set of clients may be interested in doing the Model Training for Gen AI by themselves.

## Watsonx aaS on IBM Cloud

{: #deployment-watsonx-Aas}

Customers can use the IBM Cloud watsonx-aaS service without the need to deploy any generative AI software. IBM Cloud IaaS, PaaS services provide the supporting/surround environment for a secure and regulatory compliant development and deployment of the generative AI workloads/solutions for inferencing, prompt tuning and fine tuning.

https://cloud.ibm.com/docs/watson?topic=watson-about#about

https://www.ibm.com/downloads/cas/1X7EPRYE

## Maximo Visual Inspection

The **IBM® Maximo® Visual Inspection** platform, built on cognitive infrastructure, is a new generation of video and image analysis platforms. The platform offers built-in deep learning models that learn to analyze images and video streams for classification, object detection, and anomaly detection.

![Maximo Vision.](image/architecture-image-classification-on-ibmcloud.svg "Maximo"){: caption="Figure 1. Vision RAG Pattern" caption-side="bottom"}

**Maximo Visual Inspection** includes tools and interfaces for anyone who has limited skills in deep learning technologies. You can use **IBM Maximo Visual Inspection** to label images and videos that can be used to train and validate a model. The model can then be validated and deployed in customized solutions that demand image classification, object detection, and anomaly detection.

### GPU supported on IBM Cloud for SaaS

Link to GPU supported on IBM Cloud

### Integrating with** **Maximo Visual Inspection Edge

**Maximo Visual Inspection Edge** is a web-based application that you can integrate with **Maximo Visual Inspection** to perform AI-based inspections at the edge. You can collect images to train AI models or use trained models to inspect images from cameras that are positioned close to edge activities, such as assembly-line operations.

**Maximo Visual Inspection Edge** uses data sets and trained models that are stored in** **Maximo Visual Inspection**. In **Maximo Visual Inspection Edge**, you create inspections that process images from input sources, such as cameras or network folders. These inspections either collect images to train models or use trained models and rules to inspect images. You specify the data sets where you want to store the processed images so that models can be refined and retrained.

https://www.ibm.com/docs/en/mas-cd/maximo-vi/continuous-delivery?topic=maximo-visual-inspection-edge

![Visual Inspection for image and Video.](image/video-ingestion.drawio.svg "Image and Video analysis"){: caption="Figure 1. Video and images  RAG Pattern" caption-side="bottom"}

## Watson Speech:

**IBM Cloud Speech to Text service**

![Watson Speech.](image/speech-to-text-transcription-pipeline.svg "Watson Speech"){: caption="Figure 1. Speech to Text transcription pipeline" caption-side="bottom"}

IBM Cloud Speech to Text service converts the human voice into the written word. The service uses deep-learning artificial intelligence to apply knowledge of grammar, language structure, and the composition of audio and voice signals to accurately transcribe human speech. It can be used in applications such as voice-automated chatbots, analytic tools for customer-service call centers, and multi-media transcription, among many others.

The service is available in multiple languages.

...
https://cloud.ibm.com/docs/speech-to-text?topic=speech-to-text-gettingStarted

**IBM Cloud Text to Speech service**

IBM Cloud Text to Speech service converts written text to natural-sounding speech. The service streams the synthesized audio back with minimal delay. The audio uses appropriate cadence and intonation for its language and dialect to provide voices that are smooth and natural. The service can be used in applications such as voice-automated chatbots, as well as a variety of voice-driven and screenless applications, such as tools for the disabled or visually impaired, video narration and voice over, and educational and home-automation solutions.

...

https://cloud.ibm.com/docs/text-to-speech?topic=text-to-speech-gettingStarted

https://cloud.ibm.com/docs/text-to-speech?topic=text-to-speech-speech-install-data

https://cloud.ibm.com/docs/speech-to-text?topic=speech-to-text-speech-install-data

https://cloud.ibm.com/docs/openwhisk?topic=openwhisk-pkg_text_to_speech

https://cloud.ibm.com/docs/text-to-speech?topic=text-to-speech-gettingStarted

https://cloud.ibm.com/docs/speech-to-text?topic=speech-to-text-gettingStarted

https://cloud.ibm.com/docs/speech-to-text

https://dataplatform.cloud.ibm.com/docs/content/svc-welcome/wstt.html?context=cpdaas

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
