---
title: Certain labels are deprecated for AKS nodes
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Replace the deprecated labels with the recommended substitutes.

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

The following labels are planned for deprecation with the release of Kubernetes `v1.24`. Users should change any label references to the recommended substitute.

## Why does this exist? (Root Cause)

AKS follows a release schedule where specific versions reach EOL when a specific number of  newer versions are released. The following labels are planned for deprecation with the release of Kubernetes `v1.24`. 

| Label                                    | Recommended substitute              | Maintainer               |
| :--------------------------------------- | :---------------------------------- | :----------------------- |
| failure-domain.beta.kubernetes.io/region | topology.kubernetes.io/region       | Kubernetes               |
| failure-domain.beta.kubernetes.io/zone   | topology.kubernetes.io/zone         | Kubernetes               |
| beta.kubernetes.io/arch                  | kubernetes.io/arch                  | Kubernetes               |
| beta.kubernetes.io/instance-type         | node.kubernetes.io/instance-type    | Kubernetes               |
| beta.kubernetes.io/os                    | kubernetes.io/os                    | Kubernetes               |
| node-role.kubernetes.io/agent            | kubernetes.azure.com/role=agent     | Azure Kubernetes Service |
| kubernetes.io/role                       | kubernetes.azure.com/role           | Azure Kubernetes Service |
| agentpool                                | kubernetes.azure.com/agentpool      | Azure Kubernetes Service |
| storageprofile                           | kubernetes.azure.com/storageprofile | Azure Kubernetes Service |
| storagetier                              | kubernetes.azure.com/storagetier    | Azure Kubernetes Service |
| accelerator                              | kubernetes.azure.com/accelerator    | Azure Kubernetes Service |

## Additional Resources

See AKS documentation: [Use labels in an Azure Kubernetes Service](https://learn.microsoft.com/en-gb/azure/aks/use-labels#deprecated-labels)