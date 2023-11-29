---
title: Incompatibility between Redis Enterprise versions and Kubernetes versions.
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

We strongly recommend upgrading your cluster’s Kubernetes version to a compatible version per the guidance of Redis Labs.

Redis Enterprise follows a release schedule where with each release the supported Kubernetes distributions are updated. Following are the supported distributions for the current release.

| Kubernetes Version   | 1.22       | 1.23       | 1.24      | 1.25      | 1.26      | 1.27      |
| :------------------- | :--------- | :--------- | :-------- | :-------- | :-------- | :-------- |
| Community Kubernetes |            | Deprecated | Supported | Supported | Supported | Supported |
| Amazon EKS           | Deprecated | Deprecated | Supported | Supported |           |           |
| AKS                  |            | Deprecated | Supported | Supported | Supported |           |
| GKE                  | Deprecated | Deprecated | Supported | Supported | Supported |           |
| Rancher 2.6          | Deprecated | Deprecated | Supported |           |           |           |
| Rancher 2.7          |            | Deprecated | Supported |           |           |           |
| VMWare TKG 1.6       | Deprecated | Deprecated |           |           |           |           |

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

The version of Kubernetes your cluster is running is incompatible with your version of Redis Enterprise which means you cannot receive technical support and the software may have incompatibilities leading to unknown behavior. 

## Why does this exist? (Root Cause)

Redis Enterprise follows a release schedule where with each release the supported Kubernetes distributions are updated.

## Additional Resources

For more information see: [Redis Enterprise Operator Supported Distributions](https://docs.redis.com/latest/kubernetes/reference/supported_k8s_distributions/)