---
copyright:
  years: 2024
lastupdated: "2024-08-29"

subcollection: pattern-watson-speech-vision

keywords:
---
{{site.data.keyword.attribute-definition-list}}

# Service management design considerations
{: #service}

The following summarizes the service management design considerations for the speech and vision recognition with RAG AI pattern.

## Requirements
{: #service-management-requirements}

- Manage and monitor AI
- Enable logging and alerting to DevOps tools
- Manage and monitor IBM Cloud VPC VSI workloads
- Manage and monitor container workloads on {{site.data.keyword.Bluemix_notm}}
- Provide infrastructure and platform logs and audit
- Manage and monitor models

## Design considerations
{: #monitoring-considerations}

Review the key design considerations for service management

### {{site.data.keyword.IBM_notm}} Logs
{: #log-analysis}

You can use {{site.data.keyword.IBM_notm}} Logs to add log management capabilities:

- Customizable user interface for live streaming of log tailing, real-time troubleshooting issue alerts, and log archiving.
- Quick integration with the cluster through a script.
- Aggregated logs across clusters and cloud providers.
- Historical access to logs.
- Highly available, scalable, and compliant with industry security standards.
- Integrated with {{site.data.keyword.Bluemix_notm}} IAM for user access management.

### {{site.data.keyword.Bluemix_notm}} Monitoring
{: #ibm-cloud-monitoring}

The recommended approach for multi-cluster management and monitoring is to use {{site.data.keyword.Bluemix_notm}} tools that include {{site.data.keyword.IBM_notm}} Log Analysis and {{site.data.keyword.Bluemix_notm}} Monitoring. This approach enables application cluster metrics log aggregation and central management within {{site.data.keyword.Bluemix_notm}}.

You can use {{site.data.keyword.Bluemix_notm}} Monitoring to monitor the performance and overall system health:

- Customizable user interface for a unified view of cluster metrics, container security, resource usage, alerts, and custom events.
- Quick integration with the cluster through a script.
- Aggregated metrics and container monitoring across clusters and cloud providers.
- Historical access to metrics that is based on the timeline and plan, and the ability to capture and download trace files.
- Highly available, scalable, and compliant with industry security standards.
- Integrated with {{site.data.keyword.Bluemix_notm}} IAM for user access management.

### Flow logs for VPC clusters
{: #flow-logs}

Configure {{site.data.keyword.Bluemix_notm}} Flow Logs for VPC to gather information about the traffic entering or leaving VPC. Flow logs are stored in an {{site.data.keyword.Bluemix_notm}} Object Storage instance and can be used for troubleshooting purposes, adhering to compliance regulations. For more information, see [Flow logs](https://cloud.ibm.com/docs/vpc?topic=vpc-flow-logs).

### IBM Cloud watsonx management capabilities
{: #watsonx-capabilities-management}

- Model management: watsonx governance allows you to manage multiple AI models within a single platform, making it easier to track model performance, update models, and retire old versions.
- Monitoring dashboards: The watsonx governance console provides intuitive dashboards that offer real-time insights into your AI-powered application's performance. You can monitor key metrics such as accuracy, latency, and throughput.
- Alerting and notifications: Set up custom alerts for specific events or thresholds, helping ensure you're always informed about potential issues or anomalies in your AI models' behavior.
- Model explainability: watsonx governance provides features to explain the decision-making processes of your AI models, enabling transparency and trustworthiness.
- Risk analysis: watsonx offers advanced risk analysis capabilities to identify potential biases and other risks associated with your AI-powered applications.
- Security auditing: watsonx governance built-in security auditing mechanisms help you detect vulnerabilities in your AI models and help ensure compliance with relevant regulations.
- Model versioning: watsonx governance allows to manage multiple versions of your AI models, allowing for easy tracking of changes, updates, and rollbacks if needed.
- Integration with other {{site.data.keyword.IBM_notm}} tools: Seamlessly integrate watsonx with other IBM tools like Cloud Pak, Watson Studio, and other customer management environment.

### IBM Watson voice assistant
{: watson-voice-assistant-managment}

- leverages IBM Cloud speech to text and text to speech services.
- Speech detection features: You can use speech handling through trigger events when speech starts, monitor pauses by using silence detectors, and handle timeouts during streaming.
- Real-time updates: Use WebSocket APIs for real-time transcription and interim results. Low-latency modes can be enabled for faster response times, although this may slightly reduce accuracy.
- Background suppression and sensitivity: Adjust parameters for background noise suppression and speech detector sensitivity to manage noisy environments or varying speech quality [IBM Watson speech features](/docs/speech-to-text?topic=speech-to-text-service-features) and [IBM Watson getting started](/docs/services/speech-to-text?topic=speech-to-text-gettingStarted).

For more information, see the following:

- [{{site.data.keyword.IBM_notm}} Speech to Text getting started](/docs/services/speech-to-text?topic=speech-to-text-gettingStarted)
- [{{site.data.keyword.IBM_notm}} Text to Speech Overview](https://cloud.ibm.com/catalog/services/text-to-speech){: external}
