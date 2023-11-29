---
title: Incompatibility between ExternalDNS and K8s versions
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Move to the ExternalDNS version as per the official documentation. 

| ExternalDNS                           | \<= 0.9.x | >= 0.10.0 |
| :------------------------------------ | :-------- | :-------- |
| Kubernetes \<= `v1.18`                | ✅         | ❌         |
| Kubernetes >= `v1.19` and \<= `v1.21` | ✅         | ✅         |
| Kubernetes >= `v1.22`                 | ❌         | ✅         |

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

The ExternalDNS you’re running is not compliant and compatible with your Kubernetes cluster version. 

## Why does this exist? (Root Cause)

The ExternalDNS community publishes compatibility matrices of ExternalDNS Add-On and Kubernetes to make sure you run tested and qualified versions of ExternalDNS. 

## Additional Resources

For more details please refer to the official [ExternalDNS documentation](https://github.com/kubernetes-sigs/external-dns#kubernetes-version-compatibility)