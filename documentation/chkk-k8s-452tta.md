---
title: The detected Keptn version is not compatible with your Kubernetes version
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Upgrade Keptn to version that is compatible with your Kubernetes version as shown in the table below.

| Keptn Version | Supported GKE Versions | Supported AKS Versions | Supported EKS Versions |
| :------------ | :--------------------- | :--------------------- | :--------------------- |
| `v0.19`       | `v1.24 - v1.19`        | `v1.24 - v1.19`        | `v1.24 - v1.19`        |
| `v0.18`       | `v1.24 - v1.19`        | `v1.24 - v1.19`        | `v1.24 - v1.19`        |

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Running an unsupported version combination of Keptn and Kubernetes can lead to unintended behavior and functionality may not work as expected.

## Why does this exist? (Root Cause)

Keptn recommends using a supported version of Kubernetes control plane.

## Additional Resources

For more information see: [Keptn-Kubernetes compatibility matrix](https://keptn.sh/docs/install/k8s-support/#supported-versions)