---
title: Stale service proxy rules on deletion of a backend pod on AKS Kubernetes v1.24.
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Upgrade to AKS K8S version `v1.24.6` or above.

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

This regression causes stale proxy rules to be left over when a backend pod is deleted and may lead to occasional connectivity issues and timeouts, if a stale load balancing rule is matched and it redirects traffic to an endpoint which no longer exists.

## Why does this exist? (Root Cause)

On Windows nodes running AKS Kubernetes versions above `v1.24.0` (inclusive) and below `v1.24.6` deletion of a backend pod will leave behind an external VIP load balancing rule that references endpoints which no longer exist. This is caused due to the winkernel proxier setting the wrong Host Networking Service (HNS) LoadBalancer ID.

## Who is impacted and when? (Trigger Conditions)

Running a windows node on AKS Kubernetes versions `>= v1.24.0` and `< v1.24.6` and running a LoadBalancer service can trigger this Latent Availability Risk.

_Affected Versions_  
All AKS versions `>=v1.24.0` and `<v1.24.6`

## Additional resources

For more details, please refer to the following links:

- <https://github.com/kubernetes/kubernetes/issues/112836>
- <https://github.com/Azure/AKS/issues/3246>