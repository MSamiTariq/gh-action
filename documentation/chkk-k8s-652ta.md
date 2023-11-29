---
title: Docker is no longer supported as a container runtime on Windows for AKS clusters
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Upgrade all existing node pools in a cluster to use the containerd runtime for all Windows Server node pools

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Docker as a container runtime for AKS nodes running on windows is no longer covered by the AKS support policies.

## Why does this exist? (Root Cause)

AKS recommends using containerd as it is their officially supported kubernetes runtime.

## Additional Resources

For more details, please refer to the official [AKS documentation](https://learn.microsoft.com/en-gb/azure/aks/learn/quick-windows-container-deploy-cli)