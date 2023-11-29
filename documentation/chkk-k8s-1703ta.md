---
title: Incompatible version of Kubernetes with OPA Gatekeeper.
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

We strongly recommend upgrading to a Kubernetes version supported by OPA Gatekeeper.

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Running OPA Gatekeeper on an unsupported version of Kubernetes will lead to an unintended behavior and functionality may not work as expected.

## Why does this exist? (Root Cause)

The minimum Kubernetes version requirement to run OPA Gatekeeper is n-2 of the latest stable Kubernetes release as per [Kubernetes Supported Versions Policy.](https://kubernetes.io/releases/version-skew-policy/). If you are running a managed cluster by EKS, GKE or AKS, please see the relevant documentation links as given below:  
[Amazon EKS Kubernetes versions](https://docs.aws.amazon.com/eks/latest/userguide/kubernetes-versions.html)  
[GKE release schedule](https://cloud.google.com/kubernetes-engine/docs/release-schedule)  
[AKS Supported Kubernetes versions](https://learn.microsoft.com/en-us/azure/aks/supported-kubernetes-versions?tabs=azure-cli#aks-kubernetes-release-calendar)

## Additional Resources

For more information see [Gatekeeper Documentation](https://open-policy-agent.github.io/gatekeeper/website/docs/install/#minimum-kubernetes-version)