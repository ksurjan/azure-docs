---
title: Common questions about Service Fabric managed clusters 
description: Frequently asked questions about Service Fabric managed clusters, including capabilities, use cases, and common scenarios.
ms.topic: troubleshooting
ms.author: micraft
author: micraft
ms.date: 7/14/2021
ms.custom: references_regions
---

# Service Fabric managed clusters frequently asked questions

Here are some frequently asked questions (FAQs) and answers for Service Fabric managed clusters.

## General

### What are Service Fabric managed clusters?

Service Fabric managed clusters are an evolution of the Service Fabric cluster resource model designed to make it easier to deploy and manage clusters. A Service Fabric managed cluster uses the Azure Resource Manager encapsulation model so that a user only needs to define and deploy a single cluster resource compared to the many independent resources that they must deploy today (Virtual Machine Scale Set, Load Balancer, IP, and more).

### What regions are supported?

Service Fabric managed clusters are supported in all public cloud regions.

### Can I do an in-place migration of my existing Service Fabric cluster to a managed cluster resource?

No. You will need to create a new Service Fabric cluster resource to use the new Service Fabric managed cluster resource type.

### Is there an additional cost for Service Fabric managed clusters?

No. There is no additional cost associated with a Service Fabric managed cluster beyond the cost of the underlying compute, storage, and networking resources that are required for the cluster.

### Is there a new SLA introduced by the Service Fabric managed cluster resource?

The SLA doesn't change from the current Service Fabric resource model.

### What is the difference between a Basic, and Standard SKU cluster?

A Basic SKU cluster means, most of the configurations are provided by the Service Fabric resource provider. Basic SKU clusters are intended to be used for testing and pre production environments. A Standard SKU cluster allows users to configure the cluster to specifically meet their needs. For more information, see [Service Fabric managed cluster SKUs](./overview-managed-cluster.md#service-fabric-managed-cluster-skus).

## Cluster Deployment and Management

### I run custom script extensions on my Virtual Machine Scale Set, can I continue to do that with a managed Service Fabric resource?

Yes, you can specify VM extensions on managed cluster node types. For more information, see [Add a scale set extension to a Service Fabric managed cluster node type](./how-to-managed-cluster-vmss-extension.md).

### I want to have an internal-only load balancer, is that possible?

No. It isn't currently possible to have an internal-only load balancer. We recommended locking down the Network Security Group (NSG) rules to block any undesired inbound/outbound traffic.

### Can I autoscale my cluster?

Autoscaling is not currently supported.

### Can I deploy my cluster across availability zones?

Yes, Service Fabric managed clusters which span availability zones are supported in Azure regions which support availability zones. For more information, see [Service Fabric managed clusters across availability zones](./how-to-managed-cluster-availability-zones.md).

### Can I deploy stateless node types on a Service Fabric managed cluster? 

Yes, Service Fabric managed clusters support stateless node types for any secondary node types. For more information, see [Service Fabric managed cluster stateless node types](./how-to-managed-cluster-stateless-node-type.md)

### Can I select between automatic and manual upgrades for my cluster runtime?

Yes, you can select between automatic and manual upgrades. For more information, see [cluster upgrades](./how-to-managed-cluster-upgrades.md).

## Applications

### Is there a local development experience for Service Fabric managed clusters?

The local development experience remains unchanged from existing Service Fabric clusters. For more information, see [Set up your development environment](./service-fabric-get-started.md) for more details on the local development experience.

### Can I deploy my applications as an Azure Resource Manager resource?

Yes. Support has been added to deploy applications as an Azure Resource Manager resource (in addition to deployment using PowerShell and CLI). To get started, see [Deploy a Service Fabric managed cluster application using ARM template](./how-to-managed-cluster-app-deployment-template.md).

### Can I deploy applications with managed identities?

 Yes, applications with managed identities can be deployed to a Service Fabric managed cluster. For more information see, [Application managed identities](./concepts-managed-identity.md).