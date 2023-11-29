---
title: The detected KubeVirt version is not compatible with your Kubernetes version
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Use a version of KubeVirt that is supported for Kubernetes version. Each KubeVirt release maintains compatibility with the latest 3 Kubernetes releases that are out at the time the KubeVirt release is made.

The table below lists a few releases and can be used as a reference.

| KubeVirt Version |  Kubernetes Versions  |
| :--------------: | :-------------------: |
|      `v1.1`      | `v1.28, v1.27, v1.26` |
|      `v1.0`      | `v1.27, v1.26, v1.25` |
|      `v0.59`     | `v1.26, v1.25, v1.24` |
|      `v0.58`     | `v1.25, v1.24, v1.23` |
|      `v0.57`     | `v1.25, v1.24, v1.23` |
|      `v0.56`     | `v1.24, v1.23, v1.22` |
|      `v0.55`     | `v1.24, v1.23, v1.22` |
|      `v0.54`     | `v1.24, v1.23, v1.22` |
|      `v0.53`     | `v1.24, v1.23, v1.22` |
|      `v0.52`     | `v1.23, v1.22, v1.21` |
|      `v0.51`     | `v1.23, v1.22, v1.21` |
|      `v0.50`     | `v1.23, v1.22, v1.21` |

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Running an unsupported version combination of KubeVirt and Kubernetes can lead to unintended behavior and functionality may not work as expected.

## Why does this exist? (Root Cause)

KubeVirt recommends using a supported version of Kubernetes control plane. 

## Additional resources

For more information see: [KubeVirt's Kubernetes Version Compatibility](https://github.com/kubevirt/kubevirt/blob/main/docs/kubernetes-compatibility.md)