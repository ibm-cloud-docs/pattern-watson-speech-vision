---
copyright:
  years: 2024
lastupdated: "2024-03-14"

subcollection: pattern-watson-speech-vision

keywords:
---
# Architecture decisions for resiliency
{: #ad-resiliency}

The following sections summarize the resiliency architecture decisions for customer workloads deployed on {{site.data.keyword.cloud_notm}} VPC and Red Hat OpenShift. The {{site.data.keyword.Bluemix_notm}} SaaS services such as watsonx, watsonx.assistant for voice (Speech to text and Text to Speech), Maximo {{site.data.keyword.Bluemix_notm}} databases being highly available by default and their disaster recovery being solely done by backing up and restoring their data, there is no actual architecture decisions for them.

| Architecture decision                                                               | Requirement                                                                                      | Options                                                                                                                                              | Decision                             | Rationale                                                                                               |
| ----------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------ | ------------------------------------------------------------------------------------------------------- |
| High Availability for Red Hat OpenShift                                                          | Provide high availability for the container workloads                                            | Multi-zone Region Red Hat OpenShift deployment \n - Multiple Red Hat OpenShift clusters behind a global load balancer                                                       | Multi-zone Region Red Hat OpenShift deployment    | Lower deployment and management complexity and smaller footprint                                        |
| High Availability for VPC                                                           | Provide high availability for the {{site.data.keyword.Bluemix_notm}} VPC virtual server instance | Within an Availability Zone (native) \n - Within a region by using duplicate virtual server instances with a network or application load balancer | Within an Availability Zone (native) | Default native high availability within an availability zone, choice will depend on the SLA requirement |
| {: caption="Table 1. Architecture decisions for resiliency" caption-side="bottom"} |                                                                                                  |                                                                                                                                                      |                                      |                                                                                                         |
