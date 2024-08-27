---
copyright:
  years: 2024
lastupdated: "2024-03-14"

subcollection: pattern-watson-speech-vision

keywords:
---
{{site.data.keyword.attribute-definition-list}}

# Requirements

* Automation of the application build, test, and deployment process
* Reduced manual effort during deploymeny and risk of human error
* Increased speed of delivery and time-to-market
* Improved quality and reliability of software applications

## DevOps tools

{: #devops-design}

{{site.data.keyword.Bluemix_notm}} offers a comprehensive suite of DevOps tools designed to streamline the development, deployment, and management of applications. Here are some key DevOps tools available on {{site.data.keyword.Bluemix_notm}}.

### Continuous Integration

Continuous Integration (CI) in {{site.data.keyword.Bluemix_notm}} refers to the practice of automatically building, testing, and verifying the quality of software code changes as soon as they are committed to a repository. This process helps to ensure that the code is stable, secure, and functions as expected, reducing the risk of errors and defects that can occur later in the development lifecycle.

For details about Continuous Integration refer to this [section in {{site.data.keyword.Bluemix_notm}} Docs](https://www.ibm.com/topics/continuous-integration)
{: note}

Overall, Continuous Integration in {{site.data.keyword.Bluemix_notm}} helps to streamline the software development process, improve code quality, and reduce the risk of errors and defects, allowing developers to deliver high-quality applications faster and more efficiently.

### {{site.data.keyword.Bluemix_notm}} Continuous Delivery

* Toolchains:

* Toolchains integrate various tools to automate all stages of software development and deployment. You can include tools like GitHub for version control, Jenkins for continuous integration, and Slack for team communication. This integration streamlines workflows and ensures consistent, automated processes across your DevOps pipeline.

* Delivery Pipeline:

* The Delivery Pipeline service allows you to automate the build, test, and deploy phases of your application. It supports custom scripts and integrates with other tools to enable continuous integration and continuous deployment (CI/CD).

For getting started with {{site.data.keyword.Bluemix_notm}} Continuous Delivery refer to this [section in {{site.data.keyword.Bluemix_notm}} Docs](https://cloud.ibm.com/docs/ContinuousDelivery?topic=ContinuousDelivery-getting-started)
{: note}

### {{site.data.keyword.Bluemix_notm}} Container Registry

{{site.data.keyword.Bluemix_notm}} Container Registry is a managed container registry service that allows you to store, manage, and deploy container images, such as Docker images, in a secure and scalable manner.

For details about {{site.data.keyword.Bluemix_notm}} Container Registry refer to this [section in {{site.data.keyword.Bluemix_notm}} Docs]https://cloud.ibm.com/docs/Registry?topic=Registry-getting-started)
{: note}

By using {{site.data.keyword.Bluemix_notm}} Container Registry, you can streamline your container management and deployment processes, improve security and scalability, and accelerate the development and deployment of your containerized applications.

### {{site.data.keyword.Bluemix_notm}} DevOps Insights

* DevOps Insights provides data-driven insights into your code quality and the health of your DevOps processes. It aggregates data from various tools (like Git, Jenkins, and SonarQube) to give you a comprehensive view of your project's status and performance, enabling better decision-making and improving software quality.

For working {{site.data.keyword.Bluemix_notm}} DevOps Insights refer to this [section in {{site.data.keyword.Bluemix_notm}} Docs](https://cloud.ibm.com/docs/ContinuousDelivery?topic=ContinuousDelivery-di_working)
{: note}

### Tekton Pipelines

* Tekton is an open-source framework for creating cloud-native CI/CD pipelines. Integrated with {{site.data.keyword.Bluemix_notm}} Continuous Delivery, it allows you to define and run pipelines that automate the building, testing, and deploying of applications.

For working {{site.data.keyword.Bluemix_notm}} Tekton Pipelines refer to this [section in {{site.data.keyword.Bluemix_notm}} Docs](https://cloud.ibm.com/docs/ContinuousDelivery?topic=ContinuousDelivery-tekton-pipelines&interface=ui)
{: note}
