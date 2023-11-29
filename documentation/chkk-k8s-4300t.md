---
title: PodSecurityPolicy removed from Kubernetes in version 1.25
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Before upgrading your Kubernetes version to `v1.25` or greater, migrate from PodSecurityPolicy to the Built-In PodSecurity Admission Controller.  
Refer to [this](https://kubernetes.io/docs/tasks/configure-pod-container/migrate-from-psp/) migration guide by Kubernetes for more information.

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation for this ARSig.

## What is the impact? (Availability Impact)

Upgrading to Kubernetes `v1.25` or above will remove all PodSecurityPolicy resources from your cluster which puts the cluster at a higher risk of malicious or rogue containers being deployed, which can potentially compromise the availability of the entire cluster.

## Why does this exist? (Root Cause)

PodSecurityPolicy is a critical security feature that allows administrators to define and enforce security policies for the containers running inside a pod.

The decision to remove PodSecurityPolicy from Kubernetes `v1.25` was made as part of a larger effort to streamline and simplify the Kubernetes codebase. From the official [Kubernetes website](https://kubernetes.io/blog/2021/04/06/podsecuritypolicy-deprecation-past-present-and-future/):  
The way PSPs are applied to Pods has proven confusing to nearly everyone that has attempted to use them. It is easy to accidentally grant broader permissions than intended, and difficult to inspect which PSP(s) apply in a given situation.

## Who is impacted and when? (Trigger Conditions)

_Affected Versions_  
All Kubernetes Cluster versions `>= v1.25` contain this Latent Availability Risk.

## Additional Resources

For more details, please refer to the following:

- [PodSecurityPolicy Removal notice](https://kubernetes.io/docs/concepts/security/pod-security-policy/)
- [PodSecurityPolicy Deprecation: Past, Present, and Future](https://kubernetes.io/blog/2021/04/06/podsecuritypolicy-deprecation-past-present-and-future/)
- [Migration guide from PodSecurityPolicy to the Built-In PodSecurity Admission Controller](https://kubernetes.io/docs/tasks/configure-pod-container/migrate-from-psp/)