---
title: Deployment Options | MuleSoft Documentation
source: https://docs.mulesoft.com/runtime-manager/deployment-strategies
author: 
published: 
created: 2024-11-01
description: MuleSoft Documentation Site
tags:
  - EA
  - Integration
  - MuleSoft
  - iPaaS
---

Mule applications that run in the Anypoint Studio or Anypoint Code Builder IDEs deploy to an embedded test server in within the IDE. Because this server is not meant for production deployment and uptime restrictions apply, deploy your Mule applications using one of the deployment options supported by Anypoint Runtime Manager.

## CloudHub 2.0

CloudHub 2.0 is a fully managed, containerized integration platform as a service (iPaaS) where you can deploy APIs and integrations as lightweight containers in the cloud.

## CloudHub

CloudHub is a complete integration platform as a service (iPaaS) that provides server functionality for you to deploy your applications without having to configure a hosting environment. Based on your contract, you control how many resources to assign to your application.

You can deploy your applications from the [Anypoint Platform![Leaving the Site](https://docs.mulesoft.com/_/img/icons/external-link.svg "Leaving the Site")](https://anypoint.mulesoft.com/) Runtime Manager cloud console and host them in [CloudHub](https://docs.mulesoft.com/cloudhub/). For more information on how to deploy applications to CloudHub, see [Deploy to CloudHub](https://docs.mulesoft.com/cloudhub/deploying-to-cloudhub).

## Hybrid Deployments

With the hybrid deployment option, you deploy your applications from the Runtime Manager cloud console to your Mule servers and use Runtime Manager to manage them. This option provides you with flexibility and control over your on-premises security but requires you to provide the hosting infrastructure.

To use the hybrid option, you first register your Mule servers with the Runtime Manager agent. Then, from Runtime Manager, you can optionally add those servers to server groups or clusters to provide high availability. Finally, you deploy your applications from Runtime Manager to either a server, server group, or cluster.

For more information on how to deploy applications to your Mule servers, see [Deploy to Your Servers](https://docs.mulesoft.com/deploying-to-your-own-servers).

## Anypoint Platform Private Cloud Edition

[Anypoint Platform Private Cloud Edition](https://docs.mulesoft.com/private-cloud/latest/) is a containerized distribution of the management and engagement capabilities of Anypoint Platform that you host on-premises or in your organization’s private cloud environment.

If your organization has strict regulatory or compliance requirements that limit the use of cloud solutions, you can use Anypoint Platform PCE to deploy and host your applications on-premises.

For more information on how to deploy applications to Anypoint Platform Private Cloud Edition, see [Deploy to Your Servers](https://docs.mulesoft.com/deploying-to-your-own-servers).

## Anypoint Runtime Fabric Deployments

Anypoint Runtime Fabric is a container service that automates the deployment and orchestration of Mule applications and API gateways. Runtime Fabric runs within a customer-managed infrastructure on AWS, Azure, virtual machines (VMs), and bare-metal servers.

Runtime Fabric contains all of the components it requires. These components, including Docker and Kubernetes, are optimized to work efficiently with Mule runtimes and other MuleSoft services.

To use the Runtime Fabric option, you first create a Runtime Fabric using Runtime Manager. Then, you install Runtime Fabric on your infrastructure. Finally, you deploy your applications from the Runtime Manager cloud console to the Runtime Fabric you created.

## Deployment Option Icons

Icons appear at the begining of each page in the Runtime Manager documentation, indicating the deployment options to which the content applies.

| Deployment Option | Icon |
| --- | --- |
| CloudHub 2.0 | [![logo cloud2 active](https://docs.mulesoft.com/_images/logo-cloud2-active.png "CloudHub 2.0")](https://docs.mulesoft.com/runtime-manager/deployment-strategies/#cloudhub-2-deployments) |
| CloudHub | [![logo cloud active](https://docs.mulesoft.com/_images/logo-cloud-active.png "CloudHub")](https://docs.mulesoft.com/runtime-manager/deployment-strategies/#cloudhub-deployments) |
| Hybrid | [![logo hybrid active](https://docs.mulesoft.com/_images/logo-hybrid-active.png "Hybrid")](https://docs.mulesoft.com/runtime-manager/deployment-strategies/#hybrid-deployments) |
| Anypoint Platform Private Cloud Edition | [![logo server active](https://docs.mulesoft.com/_images/logo-server-active.png "Anypoint Platform PCE")](https://docs.mulesoft.com/runtime-manager/deployment-strategies/#anypoint-platform-pce-deployments) |
| Anypoint Runtime Fabric | [![logo rtf active](https://docs.mulesoft.com/_images/logo-rtf-active.png "Runtime Fabric")](https://docs.mulesoft.com/runtime-manager/deployment-strategies/#anypoint-runtime-fabric-deployments) |

## Runtime Manager Features

For an overview of the Runtime Manager features available with each deployment option, see:

- [High Availability](https://docs.mulesoft.com/runtime-manager/deployment-strategies/#high-availability)
- [Java Versions](https://docs.mulesoft.com/runtime-manager/deployment-strategies/#java-versions)
- [Load Balancing](https://docs.mulesoft.com/runtime-manager/deployment-strategies/#load-balancing)
- [Logging](https://docs.mulesoft.com/runtime-manager/deployment-strategies/#logging)
- [Monitoring](https://docs.mulesoft.com/runtime-manager/deployment-strategies/#monitoring)
- [Object Store](https://docs.mulesoft.com/runtime-manager/deployment-strategies/#object-store)
- [Scheduling](https://docs.mulesoft.com/runtime-manager/deployment-strategies/#scheduling)
- [Security Updates](https://docs.mulesoft.com/runtime-manager/deployment-strategies/#security-updates)
- [Shared Resource Support](https://docs.mulesoft.com/runtime-manager/deployment-strategies/#shared-resource-support)
- [Troubleshooting](https://docs.mulesoft.com/runtime-manager/deployment-strategies/#troubleshooting)
- [Horizontal Autoscaling](https://docs.mulesoft.com/runtime-manager/deployment-strategies/#horizontal-autoscaling)

### Load Balancing

| Deployment Option | Supported Load Balancing | Alternative/Workaround |
| --- | --- | --- |
| CloudHub 2.0 | When deploying your application to two or more replicas, the CloudHub HTTP load balancing service distributes requests across these replicas. See [Scale Out and Data Center Redundancy](https://docs.mulesoft.com/cloudhub-2/ch2-architecture#scale-out-and-data-center-redundancy). |  |
| CloudHub | If your application runs on multiple workers, the CloudHub shared load automatically balances incoming traffic. See [Dedicated Load Balancers](https://docs.mulesoft.com/cloudhub/cloudhub-dedicated-load-balancer). | Use the optional dedicated load balancer (DLB) component to route external traffic to multiple Mule applications deployed to CloudHub workers in Anypoint Virtual Private Cloud (VPC). |
| Hybrid | Not Supported. | You can manage load balancing with the tools connected to your on-premises resources. |
| Private Cloud Edition | Not Supported. | You can manage load balancing with the tools connected to your on-premises resources. |
| Runtime Fabric | Internal load balancer for basic load balancing. | You can also forward logs from Runtime Fabric to a rsyslog server. |

### Logging

| Deployment Option | Description | Alternative/Workaround | More Information |
| --- | --- | --- | --- |
| CloudHub 2.0 | CloudHub 2.0 provides access to log data that includes deployment messages and events for each replica and Mule runtime engine logs. |  | [Viewing Log Data for Deployed Apps](https://docs.mulesoft.com/cloudhub-2/ch2-view-logs) |
| CloudHub | CloudHub provides a logging service for customizing log levels, searching logs, and downloading logs. |  | [View Log Data](https://docs.mulesoft.com/cloudhub/viewing-log-data) |
| Hybrid | The Runtime Manager logging feature is not available for hybrid deployments. | You can configure on-premises applications to send data to external analytics tools, such as Splunk or ELK, to manage your logs. | [Export Data from Runtime Manager to External Analytics Tools](https://docs.mulesoft.com/sending-data-from-arm-to-external-analytics-software) |
| Private Cloud Edition | The Runtime Manager logging feature is not available for hybrid deployments. | The Runtime Manager logging feature is not available for hybrid deployments. | [Export Data from Runtime Manager to External Analytics Tools](https://docs.mulesoft.com/sending-data-from-arm-to-external-analytics-software) |
| Runtime Fabric | Runtime Fabric supports Anypoint Monitoring.   This feature is available only if your organization has the Anypoint Integration Advanced package or a Titanium subscription to Anypoint Platform. For more information, see the [Pricing and Packaging](https://docs.mulesoft.com/general/pricing) documentation. | You can also forward logs from Runtime Fabric to a rsyslog server. | [Logs](https://docs.mulesoft.com/runtime-fabric/latest/manage-monitor-applications#logs) |

### Monitoring

| Deployment Option | Implementation | Functionality | More Information |
| --- | --- | --- | --- |
| CloudHub 2.0 | \- You can create alerts in [Runtime Manager](https://docs.mulesoft.com/alerts-on-runtime-manager) for applications deployed to CloudHub 2.0.   \- You can enable trace data collection for your CloudHub 2.0 applications that are deployed to either shared or private spaces and running on Mule runtime 4.6.0 or later. | \- Run thread dumps. Configure application alerts.  \- Once you enable tracing, and redeploy the application, the Runtime Manager backend starts instrumenting traces for your application. | \- [Monitoring Apps Deployed to CloudHub 2.0](https://docs.mulesoft.com/cloudhub-2/ch2-monitor-apps)   \- [Enable Trace Data Collection](https://docs.mulesoft.com/cloudhub-2/ch2-deploy-private-space#enable-distributed-tracing) |
| CloudHub | Runtime Manager dashboards provide performance metrics for all deployed applications. | Alerts based on alert conditions on deployed applications. Standard notifications to inform you when events occur in your applications. Add a CloudHub connector to your application’s flows and set up custom alerts and notifications triggered by any event. | [Monitor Applications and Servers](https://docs.mulesoft.com/monitoring) |
| Hybrid | Runtime Manager dashboards provide performance metrics for all deployed applications. | Alerts based on alert conditions on deployed applications. Standard notifications to inform you when events occur in your applications. Alerts triggered by events related to the servers on which they run. | [Monitor Applications and Servers](https://docs.mulesoft.com/monitoring) |
| Private Cloud Edition | Anypoint Platform PCE does not support Runtime Manager dashboards. | Alerts based on alert conditions on deployed applications. Standard notifications to inform you when events occur in your applications. Alerts triggered by events related to the servers on which they run. | [Monitor Applications and Servers](https://docs.mulesoft.com/monitoring) |
| Runtime Fabric | The Runtime Fabric agent monitors Kubernetes Deployments labelled with `rtf.mulesoft.com/id`. | When Kubernetes updates the state of the deployment, the agent sends that update to the control plane. | [Monitoring Application Deployments](https://docs.mulesoft.com/runtime-fabric/latest/#monitoring-application-deployments)   [Logs](https://docs.mulesoft.com/runtime-fabric/latest/manage-monitor-applications#logs) |

### Object Store

| Deployment Option | Implementation | Note | More Information |
| --- | --- | --- | --- |
| CloudHub 2.0 | You do not need to configure your applications to use Object Store in CloudHub 2.0. Additionally, Mule 4 applications support Object Store v2, which can be enabled from Anypoint Runtime Manager console. | When you enable Object Store v2 in CloudHub 2.0, note that it is rate limited. | [Object Store v2 Overview](https://docs.mulesoft.com/object-store/) |
| CloudHub | CloudHub provides a preconfigured default object store that you can reference using Anypoint Connector for Object Store. | Idempotent routers work only with in-memory stores. | [Manage Application Data Storage with Object Stores](https://docs.mulesoft.com/cloudhub/managing-application-data-with-object-stores) |
| Hybrid | Not available for hybrid deployments. | To use object stores, you must configure a database to store data. | [Object Store Connector](https://docs.mulesoft.com/object-store-connector/latest/) |
| Private Cloud Edition | Not available for Anypoint Platform PCE deployments. | To use object stores, you must configure a database to store data. | [Object Store Connector](https://docs.mulesoft.com/object-store-connector/latest/) |
| Runtime Fabric | Not available for Runtime Fabric deployments. | To use object stores, you must configure a database to store data. | [Object Store Connector](https://docs.mulesoft.com/object-store-connector/latest/) |

### Scheduling

| Deployment Option | Implementation | Note | More Information |
| --- | --- | --- | --- |
| CloudHub 2.0 | You can use Runtime Manager to view and control the Scheduler components within the flows in your deployed applications without changing your running application. | To view the application schedules, you must have the Exchange Viewer permission, in addition to the Read Applications permission. | [Managing App Schedules](https://docs.mulesoft.com/cloudhub-2/ch2-manage-schedules) |
| CloudHub | You can use Runtime Manager to view and control the Scheduler components within the flows in your deployed applications. | You cannot manage CloudHub schedules using scripts. Use the **Schedules** tab or the CloudHub API to manage CloudHub schedules. | [Manage Schedules](https://docs.mulesoft.com/cloudhub/managing-schedules) |
| Hybrid | Not available for hybrid deployments. | To schedule tasks, use the Scheduler endpoint element in your flows. | [Scheduler Endpoint](https://docs.mulesoft.com/mule-runtime/latest/scheduler-concept) |
| Private Cloud Edition | Not available for Anypoint Platform PCE deployments | To schedule tasks, use the Scheduler endpoint element in your flows. | [Scheduler Endpoint](https://docs.mulesoft.com/mule-runtime/latest/scheduler-concept) |
| Runtime Fabric | Not available for Runtime Fabric deployments. | To schedule tasks, use the Scheduler endpoint element in your flows. | [Scheduler Endpoint](https://docs.mulesoft.com/mule-runtime/latest/scheduler-concept) |

### Security Updates

| Deployment Option | Implementation | More Information |
| --- | --- | --- |
| CloudHub 2.0 | CloudHub 2.0 regularly applies security patches as needed to ensure that your application is secure. | [CloudHub 2.0 Operating System Patch Updates](https://docs.mulesoft.com/cloudhub-2/ch2-patch-updates) |
| CloudHub | CloudHub applies security patches as needed to ensure that your application is secure and, once per month, it updates Mule to maintain the stability of your application. | [CloudHub Runtime Continuous Updates](https://docs.mulesoft.com/cloudhub/cloudhub-app-runtime-version-updates) |
| Hybrid | After an application is deployed and running, you must apply any security updates for the selected runtime version manually. | [Security for Hybrid Deployments](https://docs.mulesoft.com/runtime-manager/deployment-strategies/#security-for-hybrid-deployments) |
| Private Cloud Edition | After an application is deployed and running, you must apply any security updates for the selected runtime version manually. |  |
| Runtime Fabric | When a security update is available for the runtime version for an app, you can see and apply the update in Runtime Manager. |  |

### Shared Resource Support

| Deployment Option | Implementation | More Information |
| --- | --- | --- |
| CloudHub 2.0 | A shared space is an elastic cloud of resources that includes Mule instances running in a multi-tenant environment. CloudHub 2.0 provides one shared space in each supported region, to which you deploy your integration applications. | [Shared Spaces](https://docs.mulesoft.com/cloudhub-2/ch2-shared-space-about) |
| CloudHub | Each application deployed to CloudHub runs on a separate virtual server. You don’t need to use domains to share ports or other resources between applications. |  |
| Hybrid | When deploying on-premises, you can create `Domain` mule projects with no flows and a set of global configuration elements to share among other applications deployed to the same server. | [Shared Resource Support for On-Premises App Deployments](https://docs.mulesoft.com/runtime-manager/deployment-strategies/#shared-resource-support-for-on-premises-app-deployments) |
| Private Cloud Edition | When deploying on-premises, you can create `Domain` mule projects with no flows and a set of global configuration elements to share among other applications deployed to the same server. | [Shared Resource Support for On-Premises App Deployments](https://docs.mulesoft.com/runtime-manager/deployment-strategies/#shared-resource-support-for-on-premises-app-deployments) |

### Troubleshooting

| Deployment Option | Implementation |
| --- | --- |
| CloudHub 2.0 | CloudHub 2.0 does not support the [Insight](https://docs.mulesoft.com/insight) troubleshooting tool. Use [Anypoint Monitoring](https://docs.mulesoft.com/monitoring/) instead. |
| CloudHub | The [Insight](https://docs.mulesoft.com/insight) troubleshooting tool provides in-depth visibility into business transactions and events on your Mule applications deployed through Runtime Manager. You can enable the Insight analytics feature and specify metadata options on the Insight tab. |
| Hybrid | The [Insight](https://docs.mulesoft.com/insight) troubleshooting tool provides in-depth visibility into business transactions and events on your Mule applications deployed through Runtime Manager. |
| Private Cloud Edition | Anypoint Platform PCE does not include the [Insight](https://docs.mulesoft.com/insight) troubleshooting tool. |
| Runtime Fabric | Use Anypoint Monitoring to view information about applications deployed to Runtime Fabric. To obtain the health status of the cluster and components, use Runtime Fabric command-line tools. See [Monitoring Applications Deployed to Runtime Fabric](https://docs.mulesoft.com/runtime-fabric/latest/manage-monitor-applications). |

## Security for Hybrid Deployments

[![logo hybrid active](https://docs.mulesoft.com/_images/logo-hybrid-active.png "Hybrid")](https://docs.mulesoft.com/runtime-manager/deployment-strategies/#hybrid-deployments)

By default, only metadata pushed by the Runtime Manager agent in each Mule runtime engine flows to the cloud. No application data is exposed.

The agent monitors and controls Mule, and publishes its data to the control plane. You can control Mule from external systems by calling Runtime Manager agent APIs, or you can specify that Mule publishes its data to external systems.

You can change the default behavior so that the agent pushes IDs, final average numbers, or any data you find useful for monitoring or keeping control of applications. See [Runtime Manager Agent](https://docs.mulesoft.com/runtime-manager-agent).

[![logo hybrid active](https://docs.mulesoft.com/_images/logo-hybrid-active.png "Hybrid")](https://docs.mulesoft.com/runtime-manager/deployment-strategies/#hybrid-deployments) [![logo server active](https://docs.mulesoft.com/_images/logo-server-active.png "Anypoint Platform PCE")](https://docs.mulesoft.com/runtime-manager/deployment-strategies/#anypoint-platform-pce-deployments)

When deploying on-premises, you can create `Domain` mule projects with no flows and a set of global configuration elements to share among other applications deployed to the same server.

Use this strategy to avoid configuring the same settings and credentials for each application. You can also use it to configure multiple applications to listen on the same HTTP host and port, or other exclusive resources.

## See Also