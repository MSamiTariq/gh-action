---
title: Istio proxy version 1.9.5 should not be used
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Upgrade Istio proxy to `v1.11+` to apply the available patch. You can do so by following the upgrade steps given in Istio's Official Documentation [here](https://istio.io/latest/docs/setup/upgrade/)

## How to fix it, short-term workaround? (Mitigation)

No immediate mitigation required as Istio does not directly use the OpenSSL libraries on the host.

## What is the impact? (Availability Impact)

Istio proxy version `v1.9.5` contains the following vulnerabilities in openssl libraries: [DLA-2563-1](https://www.debian.org/lts/security/2021/dla-2563) , [DLA-2492-1](https://www.debian.org/lts/security/2020/dla-2492). This may impact the overall security posture of the cluster.

## Why does this exist? (Root Cause)

Istio proxy version `v1.9.5` contains the following vulnerabilities in openssl libraries: [DLA-2563-1](https://www.debian.org/lts/security/2021/dla-2563) , [DLA-2492-1](https://www.debian.org/lts/security/2020/dla-2492). This may impact the overall security posture of the cluster.

## Who is impacted and when? (Trigger Conditions)

_Affected Versions_  
All EKS clusters or Kubernetes clusters using Istio proxy version `v1.9.5`

_Affected Images_  
The container image tags for Istio proxy with version `v1.9.5` are affected.

e.g. `istio-proxyv2:1.9.5-distroless`

## Additional Resources

For more details on supported versions of Istio, please refer to the[ official Istio documentation here](https://istio.io/latest/news/releases/1.9.x/announcing-1.9.5/)