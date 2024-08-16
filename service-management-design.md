---
copyright:
  years: 2024
lastupdated: "2024-03-29"

subcollection: pattern-watson-speech-vision

keywords:
---
{{site.data.keyword.attribute-definition-list}}

# Service management design considerations

{: #service}

## Requirements

{: #service-management-requirements}

The following are service management requirements watsonx and enterprise workload pattern:

- Manage and monitor ai.
- Enable logging and alerting to DevOps tools.
- manage and monitor customer x86 enterprise workloads
- manage and monitor container workloads on IBM Cloud.
- provide infrastructure and platform logs and audit.

## Design considerations

{: #monitoring-considerations}

Review the key considerations for service management.

Management and monitoring

{: #management-monitoring}

The recommended approach for multi-cluster management and monitoring is to use IBM Cloud tools that include IBM Log Analysis and IBM Cloud Monitoring. This approach enables application cluster metrics log aggregation and central management within IBM Cloud.

### IBM watson x management capabilities

Here are some of the key management and monitoring features in watson x:

1. **Model Management** : watsonx governance allows you to manage multiple AI models within a single platform, making it easier to track model performance, update models, and retire old versions.
2. **Monitoring Dashboards** : The watsonx governance console provides intuitive dashboards that offer real-time insights into your AI-powered application's performance. You can monitor key metrics such as accuracy, latency, and throughput.
3. **Alerting and Notifications** : Set up custom alerts for specific events or thresholds, ensuring you're always informed about potential issues or anomalies in your AI models' behavior.
4. **Model Explainability** : watsonx governanceprovides features to explain the decision-making processes of your AI models, enabling transparency and trustworthiness.
5. **Risk Analysis** : WatsonX offers advanced risk analysis capabilities to identify potential biases and other risks associated with your AI-powered applications.
6. **Security Auditing** : watsonx governance built-in security auditing mechanisms help you detect vulnerabilities in your AI models and ensure compliance with relevant regulations.
7. **Model Versioning** : watsonx governance allows to manage multiple versions of your AI models, allowing for easy tracking of changes, updates, and rollbacks if needed.
8. **Integration with Other IBM Tools** : Seamlessly integrate WatsonX with other IBM tools like Cloud Pak, Watson Studio,and other customer management environment.

### **IBM Watson voice assistance** 

#### **watson Speech to Text**

**Management and Monitoring** :

* **Speech detection features** : You can speech handling via trigger events when speech starts, monitor pauses using silence detectors, and handle timeouts during streaming.
* **Real-Time Updates** : Use WebSocket APIs for real-time transcription and interim results. Low-latency modes can be enabled for faster response times, although this may slightly reduce accuracy.
* **Background Suppression & Sensitivity** : Adjust parameters for background noise suppression and speech detector sensitivity to manage noisy environments or varying speech quality** **([IBM Cloud](https://ondeck.console.cloud.ibm.com/docs/speech-to-text?topic=speech-to-text-service-features))** **([IBM Cloud](https://ondeck.console.cloud.ibm.com/docs/services/speech-to-text?topic=speech-to-text-gettingStarted)).

#### **watson Text to Speech**

**Management and Monitoring** :

* **Customization Options** : Use APIs to synthesize text into speech, with control over the voice (male or female, standard or neural), languages (English, Spanish, etc.), and audio formats (WAV, OGG).
* **Voice Customization** : You can define custom pronunciations, control speech synthesis attributes such as pitch and volume, and even work with IBM to create custom voices if you have specific needs** **([IBM Cloud](https://cloud.ibm.com/catalog/services/text-to-speech))** **([IBM Cloud](https://cloud.ibm.com/docs/text-to-speech?topic=text-to-speech-gettingStarted)).

#### Management and Monitoring

* Use IBM Cloud's built-in monitoring and logging tools to track API usage, errors, and performance metrics.
* For troubleshooting or enhancing performance, monitor real-time data streams, adjust parameters based on use cases, and fine-tune latency settings for faster or more accurate results.

For more detailed instructions, you can explore the following IBM Cloud documentation:

* [IBM Speech to Text Getting Started](https://cloud.ibm.com/docs/services/speech-to-text?topic=speech-to-text-gettingStarted)
* [IBM Text to Speech Overview](https://cloud.ibm.com/catalog/services/text-to-speech)

## IBM Log Analysis

{: #log-analysis}

You can use IBM Log Analysis to add log management capabilities to Red Hat OpenShift VPC clusters and provide for the following:

* Customizable user interface for live streaming of log tailing, real-time troubleshooting issue alerts, and log archiving.
* Quick integration with the cluster via a script.
* Aggregated logs across clusters and cloud providers.
* Historical access to logs.
* Highly available, scalable, and compliant with industry security standards.
* Integrated with IBM Cloud IAM for user access management.

## IBM Cloud Monitoring

{: #ibm-cloud-monitoring}

You can use IBM Cloud Monitoring to monitor the performance and overall system health of Red Hat OpenShift VPC clusters and provide for the following:

* Customizable user interface for a unified view of cluster metrics, container security, resource usage, alerts, and custom events.
* Quick integration with the cluster via a script.
* Aggregated metrics and container monitoring across clusters and cloud providers.
* Historical access to metrics that is based on the timeline and plan, and the ability to capture and download trace files.
* Highly available, scalable, and compliant with industry security standards.
* Integrated with IBM Cloud IAM for user access management.

For more information, see** **[how to forward application and cluster metric data to IBM Cloud Monitoring](https://github.ibm.com/cloud-docs-solutions/pattern-webapp-openshift-vpc/blob/review/docs/openshift?topic=openshift-health-monitor#openshift_monitoring)

## Flow Logs for VPC clusters

{: #flow-logs}

Configure IBM Cloud Flow Logs for VPC to gather information about the traffic entering or leaving VPC cluster worker nodes. Flow logs are stored in an IBM Cloud Object Storage instance and can be used for troubleshooting purposes, adhering to compliance regulations. For more information, see** **[Flow logs use cases](https://github.ibm.com/cloud-docs-solutions/pattern-webapp-openshift-vpc/blob/review/docs/vpc?topic=vpc-flow-logs&interface=ui#flow-logs-use-cases).

Using IBM Cloud Monitoring can create alerts when workloads need more resources. {: note}

## Resource Management

{: #resource-management}

Set up spending notifications from the IBM Cloud billing console. You can set quotas or resource limits on clusters and namespaces. The cluster administrators can make sure that teams that share a cluster don't consume more than their fair share of compute resources, memory and CPU, by creating a** **[Resource Quota object](https://kubernetes.io/docs/concepts/policy/resource-quotas/) for each Kubernetes namespace in the cluster. If the cluster admin sets a compute resource quota, then each container within the deployment template must specify resource requests and limits for memory and CPU, otherwise the pod creation fails.
