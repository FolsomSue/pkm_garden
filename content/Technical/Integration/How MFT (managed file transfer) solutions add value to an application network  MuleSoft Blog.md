---
title: How managed file transfer solutions add value to an application network | MuleSoft Blog
source: https://blogs.mulesoft.com/learn-apis/application-network/managed-file-transfer-solutions-application-network/
author:
  - "[[MuleSoft Blog]]"
published: 2020-02-07T12:00:00-08:00, 2020-02-07T12:00:00-08:00
created: 2024-11-01
description: MFT isn’t a basic file transfer client or server for users to manually send files. Learn how it can add value to an application network.
tags:
  - EA
  - Integration
  - MuleSoft
  - iPaaS
  - MFT
---

Reading Time: 8 minutes

In [enterprise system integrations,](https://www.mulesoft.com/resources/esb/enterprise-integration-solutions) there’s no escaping the need to include file transfers in workflows. Integrators building out an [application network](https://www.mulesoft.com/resources/api/what-is-an-application-network) in MuleSoft often need to meet various file transfer use cases involving multiple B2B partners, customers, and internal lines of business. It isn’t uncommon for large consumer goods companies to exchange millions of files per month with partners such as retailers, banks, and wholesalers.

As the volume of files and endpoints increase, it becomes increasingly risky and inefficient for companies to execute [file transfers](https://blogs.mulesoft.com/dev/anypoint-studio-dev/howto-file-based-integrations-and-transfer/) using legacy methods such as point-to-point scripts and homegrown FTP server networks. Data and files are the lifeblood of organizations and data breaches are on the rise, according to the [University of Maryland](https://eng.umd.edu/news/story/study-hackers-attack-every-39-seconds), hackers attack every 39 seconds, 2,244 times a day. Companies need a strong strategy to optimize file transfer workflows. A strategy that simplifies integration and increases security, control, and visibility.

A technology that can significantly improve system-to-system file transfer security and efficiency is a [robust managed file transfer (MFT) solution](https://blogs.mulesoft.com/dev/connectivity-dev/file-exchanges-thru-mulesoft-certified-connector-managed-file-transfer-mft/). An MFT solution with reusable endpoints, increased security and improved governance that also integrates file transfer workflows with MuleSoft out-of-the-box can provide tremendous value to an application network. 

## **This isn’t your father’s FTP server – It’s MFT**

MFT isn’t a basic file transfer client or server for users to manually send files. It is an enterprise software that automates system-to-system file transfers between a variety of file transfer clients/servers/cloud storage over multiple protocols (e.g., SFTP, HTTPS, FTPS). The value of MFT is that it provides a single system for IT to manage file transfers across the whole organization with centralized visibility and control.   

## **MFT fits into a modern enterprise architecture** 

New [hybrid integration](https://www.mulesoft.com/resources/esb/hybrid-cloud-integration-solutions) scenarios are causing many enterprise architects to set up an MFT solution alongside an integration platform, such as MuleSoft. The MFT solution is used to send and receive files on a schedule between various internal and partner systems and connect to the integration platform when files need to be transformed and processed. However, not all MFT solutions can fulfill this requirement. Companies using MuleSoft should consider an MFT solution that provides an out-of-the-box connector for Anypoint Platform to avoid the time-consuming and inefficient process of custom coding integrations.   

![](https://blogs.mulesoft.com/wp-content/uploads/img_6059c41d8f994.png)

*Figure 1* – MFT within a modern enterprise architecture.

## **Example of file transfer with iPaaS integration**

The greatest value of using MFT with an [iPaaS solution](https://www.mulesoft.com/resources/cloudhub/ipaas-integration-platform-as-a-service), such as MuleSoft, is for sending and receiving files from multiple source and target endpoints within a single integration flow. For example, a company could add hundreds of partner file transfer systems to a single workflow in the MFT and integrate all the files with a single flow in MuleSoft. The diagram below shows how an iPaaS workflow (in MuleSoft) can integrate with MFT to receive or send files from / to multiple sources and targets such as SFTP servers, Amazon S3, AS2, and EDI.  

![](https://blogs.mulesoft.com/wp-content/uploads/img_6059c41f732e8.png)

*Figure 2* – An iPaaS and MFT workflow to send/receive files from multiple file transfer endpoints.

## **Modernize file transfer with the Thru MFT Connector for MuleSoft**

A robust MFT solution to consider in your search for MFT is Thru, a provider of cloud-native secure file transfer solutions. With Thru, companies can manage file transfer workflows completely in the cloud, enable self-management for partners and quickly connect to integration flows in Anypoint Platform using the [Thru MFT Connector for MuleSoft.](https://www.thruinc.com/mft-connector-for-mulesoft/)

Using the [Thru MFT Connector](https://www.mulesoft.com/exchange/org.mule.modules/thru-transport-connector/), a file transfer workflow in Thru can be subscribed to by any number of organizations and mapped to a MuleSoft flow to enable high-volume file exchanges with no coding required. All file transfer activity within Thru is audited and made available to view in end-to-end dashboards.

![](https://blogs.mulesoft.com/wp-content/uploads/img_6059c4215fa1e.png)

*Figure 3* – File transfer workflow in Thru connected to MuleSoft.

![](https://blogs.mulesoft.com/wp-content/uploads/img_6059c4239e1d0.png)

*Figure 4* – Dashboard of file transfer statuses in Thru (all workflows integrated with MuleSoft are marked with the logo).

## **Plan your modernization strategy with the MFT buyer’s guide**

To learn more about what to look for in a modern MFT solution, download [The Ultimate Buyer’s Guide: Managed File Transfer](http://bit.ly/2SgxwDo). This guide outlines the essential elements of a must-have MFT solution to aid you in evaluating options to modernize your B2B architecture for optimized business results. The following tools included in this Buyer’s Guide will aid in your evaluation of MFT solutions:

- Top features checklist to differentiate MFT solutions.
- Current state questionnaire to identify your top file transfer challenges.
- Future requirements checklist to compare and evaluate MFT vendors.
- Steps to calculate the ROI of an MFT solution.

---