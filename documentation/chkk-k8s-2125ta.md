---
title: The detected AWS EFS CSI Driver version is not compatible with your Kubernetes version
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

We strongly recommend running an AWS EFS CSI Driver version that is compatible with your Kubernetes version as shown in the table below:



| AWS EFS CSI Driver \\ Kubernetes Version | v1.11 | v1.12 | v1.13 | v1.14 | v1.15 | v1.16 | v1.17+ |
| ---------------------------------------- | ----- | ----- | ----- | ----- | ----- | ----- | ------ |
| master branch                            | ❌     | ❌     | ❌     | ❌     | ❌     | ❌     | ✅      |
| `v1.7.x`                                 | ❌     | ❌     | ❌     | ❌     | ❌     | ❌     | ✅      |
| `v1.6.x`                                 | ❌     | ❌     | ❌     | ❌     | ❌     | ❌     | ✅      |
| `v1.5.x`                                 | ❌     | ❌     | ❌     | ❌     | ❌     | ❌     | ✅      |
| `v1.4.x`                                 | ❌     | ❌     | ❌     | ❌     | ❌     | ❌     | ✅      |
| `v1.3.x`                                 | ❌     | ❌     | ❌     | ❌     | ❌     | ❌     | ✅      |
| `v1.2.x`                                 | ❌     | ❌     | ❌     | ❌     | ❌     | ❌     | ✅      |
| `v1.1.x`                                 | ❌     | ❌     | ❌     | ✅     | ✅     | ✅     | ✅      |
| `v1.0.x`                                 | ❌     | ❌     | ❌     | ✅     | ✅     | ✅     | ✅      |
| `v0.3.0`                                 | ❌     | ❌     | ❌     | ✅     | ✅     | ✅     | ✅      |
| `v0.2.0`                                 | ❌     | ❌     | ❌     | ✅     | ✅     | ✅     | ✅      |
| `v0.1.0`                                 | ✅     | ✅     | ✅     | ❌     | ❌     | ❌     | ❌      |

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

AWS EFS CSI Driver is not compatible with the Kubernetes version you are running, which means that the software may have incompatibilities leading to unknown behavior.

## Why does this exist? (Root Cause)

Using a version of Kubernetes not compatible with AWS EFS CSI Driver introduces incompatibilities in your software and may lead to undefined behavior.

## Additional Resources

For more details, please refer to [Official AWS EFS CSI Driver Documentation](https://github.com/kubernetes-sigs/aws-efs-csi-driver#kubernetes-version-compability-matrix)