---
copyright:
  years: 2024
lastupdated: "2024-03-29"

subcollection: pattern-watson-speech-vision

keywords:
---
# Architecture decisions for service management(all)

{: \#ad-service-management}

The following sections summarize the architecture decisions for service management for the Zerto for VCF resiliency pattern.

## Monitoring Architecture Decisions

{: \#architecture decisions for monitoring}

The following summarize the architecture decisions for service management for watson ai pattern.

## Architecture decisions for ai monitoring

{: \#monitoring}

| **Architecture decision**                                                       | **Requirement**                                                                                                      | **Option**                                           | **Decision**   | **Rationale**                                                                                                                                                           |
| ------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------- | -------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Manage and monitor ai.                                                                | Model Management Monitoring Dashboards Alerting and Notifications  Model  Risk Analysis Security Auditing Model Versioning | - IBM Cloud Monitoring\\n - Bring Your Own Monitoring Tool | IBM Cloud Monitoring | IBM Cloud Monitoring collects and monitors operational metrics for cloud infrastructure as well as the cloud platform and services and provides a single view for all metrics |
| Manage and monitor speech to text and text to speech                                  | Manage and monitor speech to text and text to speech.                                                                      | - NONE                                                     | Watson Rest API      | Use WebSocket APIs for real-time transcription and interim results. Low-latency modes can be enabled for faster response times, although this may slightly reduce accuracy.   |
| {: caption="Table 1. Architecture decisions for ai monitoring" caption-side="bottom"} |                                                                                                                            |                                                            |                      |                                                                                                                                                                               |

## Architecture decisions for monitoring

{: \#monitoring}

| **Architecture decision**                                                    | **Requirement**                                                                                    | **Option**                                                                | **Decision**                    | **Rationale**                                                                                                                                                                                                                                      |
| ---------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Operational monitoring of cloud infrastructure and services                        | Monitor system health to detect issues that might impact the availability of the system and application. | - IBM Cloud Monitoring\\n - Bring Your Own Monitoring Tool                      | IBM Cloud Monitoring                  | IBM Cloud Monitoring collects and monitors operational metrics for cloud infrastructure as well as the cloud platform and services and provides a single view for all metrics                                                                            |
| Operational monitoring of applications                                             | Monitor app health to detect issues that might impact the availability of the app.                       | - IBM Cloud Monitoring\\n - Instana (SaaS) \\n - Bring Your Own Monitoring Tool | IBM Cloud Monitoring + Instana (SaaS) | Instana is used along with IBM Cloud Monitoring to get more application performance metrics and automate Application Performance Management. Instana provides data and actionable insights to monitor the applications and automate root-cause analysis. |
| {: caption="Table 2. Architecture decisions for monitoring" caption-side="bottom"} |                                                                                                          |                                                                                 |                                       |                                                                                                                                                                                                                                                          |

## Architecture decisions for logging

{: \#logging}

| **Architecture decision**                                                 | **Requirement**                                                                                       | **Option**                                                                    | **Decision**                           | **Rationale**                                                                                                                                         |
| ------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- | -------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Log monitoring of cloud infrastructure and services                             | Monitor operational logs to detect issues that might impact the availability of the system and application. | - IBM Cloud Logging\\n - Bring Your Own Logging Tool                                | IBM Cloud Logging                            | IBM Cloud Logging collects operational logs from applications, platform resources, and infrastructure and provides interfaces to view and analyze all logs. |
| Log monitoring of web app                                                       | Monitor application operational logs to detect issues that might impact the availability of the app.        | - IBM Cloud Logging\\n - Application Logging Tool \\n - Bring Your Own Logging Tool | IBM Cloud Logging + Application Logging Tool | Use the Application Logging Tool to send application logs to IBM Cloud Logging and the aggregate application-specific log details.                          |
| Log monitoring of DB                                                            | Monitor database logs to detect issues that might impact the availability of the database.                  | - IBM Cloud Logging\\n - DB Tools \\n - Bring Your Own Logging Tool                 | IBM Cloud Logging + Application Logging Tool | Use the DB tools along with IBM Cloud Logging to get more DB-specific log information.                                                                      |
| {: caption="Table 3. Architecture decisions for logging" caption-side="bottom"} |                                                                                                             |                                                                                     |                                              |                                                                                                                                                             |

## Architecture decisions for auditing

{: \#auditing}

| **Architecture decision**                                                  | **Requirement**                                                                          | **Option**                                                        | **Decision**                                  | **Rationale**                                                                                                                                                                          |
| -------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------- | --------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Audit logging                                                                    | Monitor audit logs to track changes to cloud resources and detect potential security problems. | IBM Cloud Activity Tracker\\n - Hosted Event Search \\n - Event Routing | IBM Cloud Activity Tracker\\n - Hosted Event Search | IBM Cloud Activity Tracker-Hosted Event Search provides interfaces to capture, store, view, search, and monitor user-initiated actions to provision, access, and manage IBM Cloud resources. |
| {: caption="Table 4. Architecture decisions for auditing" caption-side="bottom"} |                                                                                                |                                                                         |                                                     |                                                                                                                                                                                              |

## Architecture decisions for alerting

{: \#alerting}

| **Architecture decision**                                                  | **Requirement**                                                                                                                 | **Option**                                                    | **Decision**                                                  | **Rationale**                                                                                                                                                                                                                                                      |
| -------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Operational alerts                                                               | Provide a mechanism to identify and send notifications about operational issues that are found across application and infrastructure. | IBM Cloud Monitoring, IBM Cloud Logging, and Event notifications    | IBM Cloud Monitoring, IBM Cloud Logging, and Event notifications    | IBM Cloud Monitoring and IBM Cloud Logging support the configuration of alerts to detect operational issues and send notifications to targeted channels.\\n Event notifications are used to route the alert events to service destinations to automate response actions. |
| Audit alerts                                                                     | Provide a mechanism to identify and send notifications about issues that are found in audit logs.                                     | IBM Cloud Activity Tracker, IBM Monitoring, and Event notifications | IBM Cloud Activity Tracker, IBM Monitoring, and Event notifications | IBM Activity Tracker supports the configuration of alerts to detect audit issues and send notifications to targeted channels.\\n Event notifications are used to route the alert events to service destinations to automate response actions.                            |
| {: caption="Table 5. Architecture decisions for alerting" caption-side="bottom"} |                                                                                                                                       |                                                                     |                                                                     |                                                                                                                                                                                                                                                                          |
