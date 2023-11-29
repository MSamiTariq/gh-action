---
title: The detected KEDA version is not compatible with your Kubernetes version
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Use a version of KEDA that is supported for your version of Kubernetes. Please refer to the following table for compatible versions:

| KEDA Version | Kubernetes Versions |
| :----------- | :------------------ |
| `v2.12`      | `v1.26 - v1.28`     |
| `v2.11`      | `v1.25 - v1.27`     |
| `v2.10`      | `v1.24 - v1.26`     |
| `v2.9`       | `v1.23 - v1.25`     |
| `v2.8`       | `v1.17 - v1.25`     |
| `v2.7`       | `v1.17 - v1.25`     |

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Running an unsupported version combination of KEDA and Kubernetes will lead to unintended behavior and functionality may not work as expected.

## Why does this exist? (Root Cause)

The maintainers of KEDA recommend using a Kubernetes control plane version for which it is supported.

From the [documentation](https://keda.sh/docs/latest/operate/cluster/#kubernetes-compatibility):  
_The supported window of Kubernetes versions with KEDA is known as “N-2” which means that KEDA will provide support for running on N-2 at least.  
However, maintainers can decide to extend this by supporting more minor versions based on the required CRDs being used; but there is no guarantee._

## Additional Resources

For more information see: [KEDA Kubernetes Compatibility](https://keda.sh/docs/latest/operate/cluster/#kubernetes-compatibility)