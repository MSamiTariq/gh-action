---
title: Incompatible version of Kubernetes with Bitnami Sealed Secrets
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Use a Sealed Secrets release that is supported for your current Kubernetes version.

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Using Sealed Secrets with an unsupported version of Kubernetes is not recommended. Using in incompatible version combination may cause your software to run into issues and functionality may not work as expected.

## Why does this exist? (Root Cause)

Sealed Secrets follows a release cycle similar to Kubernetes and supports only those versions of Kubernetes that have not reached end of life. For the list of Kubernetes releases supported by your cloud provider, please refer to the links provided in the Additional Resources sections.

## Additional Resources

For more details, please refer to the following links:

- [Sealed Secrets GitHub Readme](https://github.com/bitnami-labs/sealed-secrets#compatibility-with-kubernetes-versions)
- [Upgrading Kubernetes Version in EKS Clusters](https://docs.aws.amazon.com/eks/latest/userguide/update-cluster.html)
- [Upgrading Kubernetes Version in GKE Clusters](https://cloud.google.com/kubernetes-engine/docs/how-to/upgrading-a-cluster)
- [Upgrading Kubernetes Version in AKS Clusters](https://learn.microsoft.com/en-us/azure/aks/upgrade-cluster?tabs=azure-cli)