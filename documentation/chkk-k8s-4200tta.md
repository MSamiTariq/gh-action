---
title: The detected Velero version is not compatible with your Kubernetes version
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Use a version of Velero that is supported for your version of Kubernetes. Please refer to the following table for compatible versions:

| Velero Version | Kubernetes Supported Versions |
| :------------- | :---------------------------- |
| `v1.12`        | `v1.18 - latest`              |
| `v1.11`        | `v1.18 - latest`              |
| `v1.10`        | `v1.18 - latest`              |
| `v1.9`         | `v1.18 - latest`              |
| `v1.8`         | `v1.18 - latest`              |

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Running an unsupported version combination of Velero and Kubernetes will lead to unintended behavior and functionality may not work as expected.

## Why does this exist? (Root Cause)

VMWare recommends using a Kubernetes control plane version for which Velero is supported. See [Velero compatibility matrix](https://github.com/vmware-tanzu/velero#velero-compatibility-matrix) 

## Additional Resources

For more information see: [Velero compatibility matrix](https://github.com/vmware-tanzu/velero#velero-compatibility-matrix)