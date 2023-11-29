---
title: The detected Cilium version is not compatible with your Kubernetes version
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Use a version of Cilium that is compatible with your version of Kubernetes. The table below can be used as reference:

| Cilium Version | Compatible K8S Version                                                                            |
| -------------- | ------------------------------------------------------------------------------------------------- |
| `v1.14`        | `v1.19`, `v1.20`, `v1.21`, `v1.22`, `v1.23`, `v1.24`, `v1.25`, `v1.26`, `v1.27`                   |
| `v1.13`        | `v1.16`, `v1.17`, `v1.18`, `v1.19`, `v1.20`, `v1.21`, `v1.22`, `v1.23`, `v1.24`, `v1.25`, `v1.26` |
| `v1.12`        | `v1.16`, `v1.17`, `v1.18`, `v1.19`, `v1.20`, `v1.21`, `v1.22`, `v1.23`, `v1.24`                   |
| `v1.11`        | `v1.16`, `v1.17`, `v1.18`, `v1.19`, `v1.20`, `v1.21`, `v1.22`, `v1.23`                            |

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Running a version of Cilium that is incompatible with Kubernetes can lead to unintended behavior and functionality may not work as expected.

## Why does this exist? (Root Cause)

As per they documentation,

> All Kubernetes versions listed in the table above are e2e tested and guaranteed to be compatible with this Cilium version. Older Kubernetes versions that are not listed do not have Cilium support. Newer Kubernetes versions, while not listed, will depend on the backward compatibility offered by Kubernetes.

## Additional Resources

For more details, please refer to Cilium's official documentation for supported versions:

1. [K8s Versions Compatible with Cilium v1.14](https://docs.cilium.io/en/v1.14/network/kubernetes/requirements/#kubernetes-version)
2. [K8s Versions Compatible with Cilium v1.13](https://docs.cilium.io/en/v1.13/network/kubernetes/requirements/#kubernetes-version)
3. [K8s Versions Compatible with Cilium v1.12](https://docs.cilium.io/en/v1.12/concepts/kubernetes/requirements/#kubernetes-version)
4. [K8s Versions Compatible with Cilium v1.11](https://docs.cilium.io/en/v1.11/concepts/kubernetes/requirements/#kubernetes-version)