---
title: aks-secrets-store-csi-driver containers have their CPU throttled on AKS versions less than 1.22.5
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Upgrade your AKS cluster version to `v1.22.5` or higher. Refer to the [AKS Upgrade Guide](https://learn.microsoft.com/en-us/azure/aks/upgrade-cluster?tabs=azure-cli) for more information.

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

For AKS versions earlier than `v1.22.5`, aks-secrets-store-csi-driver containers are subject to a CPU cap of 100m, which may cause slower processing.

## Why does this exist? (Root Cause)

The developers initially enforced a CPU limit of 100m on aks-secrets-store-csi-driver for AKS clusters running on versions below `v1.22.5`. However, they later updated the configuration and eliminated the limit. As a result, aks-secrets-store-csi-driver versions greater than `v1.22.4` are able to utilize all available resources for execution.

## Who is impacted and when? (Trigger Conditions)

_Affected Versions_  
All clusters using aks-secretes-store-driver versions `< v1.22.5` contain this Latent Availability Risk. 

## Additional Resources

For more information, refer to this [GitHub Issue](https://github.com/Azure/AKS/issues/2972)