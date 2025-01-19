This post is the first of a four-part series this week exploring Microsoft Arc, and how it can be used as a control plane to manage services. Check each day through Thursday for subsequent installments: ([Part 2](https://thenewstack.io/tutorial-register-and-manage-linux-servers-with-azure-arc/)), ([Part 3](https://thenewstack.io/tutorial-register-and-configure-kubernetes-clusters-with-azure-arc/)).

Over the last decade, the public cloud has evolved and matured to become the foundation of modern infrastructure. Hyperscale providers such as Amazon Web Services, Microsoft, and Google have built robust control plane and orchestration engines to handle the lifecycle of managed services such as virtual machines, containers, functions databases, Big Data clusters, IoT and edge devices, and more.

One of the key services that hyperscalers offer is a scalable observability stack that can analyze infrastructure metrics, application logs, events, and traces. While the control plane orchestrates the managed services, the observability platforms provide deep insight into the entire stack.

Public cloud providers, including Amazon, Google, and Microsoft, are now extending the control plane and the observability stack to resources provisioned and running outside their respective clouds. This trend enables managing virtual machines, Kubernetes clusters, databases, data warehouses running in the on-premises data center, or even different public cloud environments.

Anthos by Google and Azure Arc are examples of the control planes running the public cloud orchestrating and managing resources deployed in diverse environments. This investment is becoming key to delivering the promise of hybrid cloud and multicloud technologies. For example, a Linux VM deployed in Google Compute Engine (GCE) is managed by Azure. The logs and metrics from the VM are ingested into Azure Monitoring and Log Analytics. Similarly, BigQuery Omni, the multicloud flavor of BigQuery, can be deployed in AWS. Anthos can take control of Azure Kubernetes Clusters (AKS) and deploy workloads to it. All this is possible with the extension of the control plane and observability offerings.

## Azure Resource Manager — The Extensible Control Plane

The original avatar of Microsoft’s public cloud, Windows Azure, was Platform as a Service (PaaS) limited to a few use cases. When Microsoft transformed its public cloud from Windows Azure to Azure to offer IaaS and making Linux a first-class citizen, it needed a new control plane.

Azure Resource Manager (ARM) was built from the ground up as an extensible control plane and orchestration engine for not just IaaS but other managed services. Eventually, ARM became the front and center of Microsoft’s cloud strategy. The extensibility aspect of ARM made it possible to bring third-party services such as Red Hat OpenShift and Databricks to Azure and manage them like native services.

ARM brought a well-defined and clean approach to defining, provisioning, and managing the lifecycle of Azure services. Microsoft creates and manages resource providers for each of the managed services.

The building blocks of Azure, such as compute, storage, and network, act as resource providers. When we use Azure Portal or CLI, we are essentially creating an instance of a resource from one of the available resource providers. ARM templates provide a declarative mechanism for provisioning resources. Irrespective of how the resources are declared, they are provisioned and managed by Azure Resource Manager.

![](https://cdn.thenewstack.io/media/2020/11/1384ff48-arc-0.png)

If you have a valid Azure subscription, the command `az provider` lists all the available providers.

![](https://cdn.thenewstack.io/media/2020/11/3f123f2f-arc-1-1024x586.png)

Whenever an Azure managed service is announced, Microsoft adds a new resource provider associated with it. For example, when you are provisioning an Azure Container Instance (ACI) resource, you are relying on **Microsoft.ContainerInstance** resource provider.

![](https://cdn.thenewstack.io/media/2020/11/cda8fa78-arc-2-891x1024.png)

From the output of `az` CLI to create a new ACI instance, notice that the type of resource is **Microsoft.ContainerInstance/containerGroups**, which is a valid ARM resource type.

Resource Groups in Azure act as logical groupings of related resources. For example, a resource group may contain a virtual machine, the disks attached to it, the IP address, the NIC, firewall rules, and other resources associated with the VM. Resource groups act as a security boundary for a set of resources that share the same context.

![](https://cdn.thenewstack.io/media/2020/11/33460ad4-arc-3-1024x412.png)

The concept of ARM enabled Microsoft to seamlessly extend the control plane to the private cloud based on the Azure Stack family. Customers use familiar tools even while dealing with the resources running in their private cloud based on Azure Stack Hub or Azure Stack HCI.

The design of ARM, Resource Groups, and ARM Templates delivered ultimate automation and manageability to customers. Undoubtedly, ARM is one of the differentiating factors of Microsoft’s cloud strategy.

### Azure Arc — Extending ARM for Hybrid Cloud and Multicloud Scenarios

Announced at Ignite 2019, Azure Arc is a control plane that can manage virtual machines, Kubernetes clusters, and highly available database servers.

Azure Arc is built on the foundation of the Azure Resource Manager’s extensibility features. It enables customers to register Linux/Windows servers and Kubernetes clusters running outside of Azure. Arc also makes it possible to run SQL and PostgreSQL database instances in Kubernetes clusters that meet the requirements.

Azure Arc is an extension of ARM to support additional resources such as servers, Kubernetes clusters, and databases.

![](https://cdn.thenewstack.io/media/2020/11/41910b70-arc-4-1024x411.png)

External resources, including servers, clusters, and databases, are managed by new resource providers of ARM. The Linux/Windows servers are managed by **Microsoft.HybridCompute** resource provider. The providers, **Microsoft.Kubernetes** and **Microsoft.KubernetesConfiguration**, are responsible for managing Kubernetes clusters and their configuration. **Microsoft.AzureArcData** provider manages the Arc data controller for SQL and PostgreSQL databases.

![](https://cdn.thenewstack.io/media/2020/11/dee6333d-arc-5-300x271.png)

Arc has three specific focus areas:

### Azure Arc for Servers

Azure Arc enabled servers allow customers to manage Windows and Linux machines hosted outside of Azure, on the corporate network, or another cloud provider similar to how they manage native Azure virtual machines.

When an external server is connected to Azure, it becomes a connected machine and is treated as a resource in Azure. Each connected machine has a Resource ID, which is included in a resource group. It benefits from standard Azure constructs such as Azure Policy and applying tags.

The process of registering a machine with Azure Arc results in running an agent that maintains the connection with the Arc control plane. The agent sends a regular heartbeat message to the service every five minutes.

In the upcoming part of this series, I will walk you through the steps of registering servers with Azure Arc.

### Azure Arc Enabled Kubernetes

Customers can attach and configure Kubernetes clusters inside or outside of Azure by using Azure Arc enabled Kubernetes. When a Kubernetes cluster is connected to Azure Arc, it will appear in the Azure portal. It will have an Azure Resource Manager ID and a managed identity. Clusters are attached to standard Azure subscriptions, are located in a resource group, and can receive tags just like any other Azure resource.

Kubernetes clusters registered with Azure Arc can participate in GitOps through the cluster configuration agent. Based on the open source flux continuous deployment tool, Arc makes it easy to manage deployments at scale.

Azure Arc enabled Kubernetes service works with any Cloud Native Computing Foundation (CNCF) conformant distribution. Microsoft has tested Arc with some of the popular Kubernetes distributions, including RedHat OpenShift 4.3, Rancher RKE 1.0.8, Canonical Charmed Kubernetes 1.18, and AKS Engine running on Azure Stack Hub.

The third installment of this series, will have a detailed tutorial on how to register Kubernetes clusters and to configure GitOps.

### Azure Arc Enabled Data Services

Azure Arc enabled data services component brings the managed data services such as SQL managed instance and PostgreSQL Hyperscale to hybrid and multicloud environments based on Kubernetes clusters.

Since they are managed services, they receive periodic updates, patches, and new features from Microsoft. With this, On-premises databases can stay up to date while ensuring that customers maintain control. Because Azure Arc enabled data services are a subscription service, customers will no longer face end-of-support situations databases.

It’s important to note that the Kubernetes clusters running Azure Data Services need not be registered with the Arc control plane. The data services can be deployed on any Kubernetes cluster that meets the requirements.

The last part of this series will have detailed coverage of Azure Arc enabled data services.

In the [next part](https://thenewstack.io/tutorial-register-and-manage-linux-servers-with-azure-arc/), I will walk you through the steps of registering Linux VMs running in other cloud environments with Azure Arc. Stay tuned!

_Janakiram MSV’s Webinar series, “Machine Intelligence and Modern Infrastructure (MI2)” offers informative and insightful sessions covering cutting-edge technologies. Sign up for the upcoming MI2 webinar at [http://mi2.live](http://mi2.live/)._

Image via [Pixabay](https://pixabay.com/ru/photos/%d0%b3%d0%be%d1%80%d1%8b-%d0%b4%d0%be%d1%80%d0%be%d0%b3%d0%b0-%d0%bd%d0%be%d1%87%d1%8c-%d0%b2%d0%b5%d1%87%d0%b5%d1%80-%d0%bd%d0%b5%d0%b1%d0%be-%d0%be%d0%b3%d0%bd%d0%b8-691186/).