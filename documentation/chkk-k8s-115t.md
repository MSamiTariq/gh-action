---
title: Restrict multiple egress hosts in Sidecar from selecting the same service
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Upgrade Istio to `v1.10+` to apply the available patch. To upgrade your version of Istio, please follow the steps given in the Official Istio Documentation [here](https://istio.io/latest/docs/setup/upgrade/)

## How to fix it, short-term workaround? (Mitigation)

Avoid specifying multiple egress hosts in the Istio sidecar configuration.

## What is the impact? (Availability Impact)

Multiple egress hosts in the Sidecar configuration may lead to the same service being selected for unrelated traffic, disrupting the overall traffic routes in the cluster.

## Why does this exist? (Root Cause)

In Istio versions earlier than `v1.10`, multiple egress hosts defined in the Sidecar configuration can select the same service.

## Who is impacted and when? (Trigger Conditions)

_Affected Versions_  
All EKS clusters or Kubernetes clusters using Istio proxy versions earlier than `v1.10`

_Affected Images_  
The container image tags for Istio proxy with version `v1.10` running on Kubernetes `v1.22` or above are affected.

## Additional Resources

Details of the exact github issue can be found [here](https://github.com/istio/istio/issues/33765).