---
title: The detected Ingress Nginx version is not compatible with your Kubernetes version
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation))

Use a version of ingress-nginx that is supported for your version of Kubernetes. Please refer to the following table for compatible versions:

| Ingress-NGINX Version | Kubernetes Supported Versions  |
| :-------------------- | :----------------------------- |
| `v1.9.4`              | `1.28, 1.27, 1.26, 1.25`       |
| `v1.9.3`              | `1.28, 1.27, 1.26, 1.25`       |
| `v1.9.1`              | `1.28, 1.27, 1.26, 1.25`       |
| `v1.9.0`              | `1.28, 1.27, 1.26, 1.25`       |
| `v1.8.4`              | `1.27, 1.26, 1.25, 1.24`       |
| `v1.8.2`              | `1.27, 1.26, 1.25, 1.24`       |
| `v1.8.1`              | `1.27, 1.26, 1.25, 1.24`       |
| `v1.8.0`              | `1.27, 1.26, 1.25, 1.24`       |
| `v1.7.1`              | `1.27, 1.26, 1.25, 1.24`       |
| `v1.7.0`              | `1.26, 1.25, 1.24`             |
| `v1.6.4`              | `1.26, 1.25, 1.24, 1.23`       |
| `v1.5.1`              | `1.25, 1.24, 1.23`             |
| `v1.4.0`              | `1.25, 1.24, 1.23, 1.22`       |
| `v1.3.1`              | `1.24, 1.23, 1.22, 1.21, 1.20` |
| `v1.3.0`              | `1.24, 1.23, 1.22, 1.21, 1.20` |
| `v1.2.1`              | `1.23, 1.22, 1.21, 1.20, 1.19` |
| `v1.1.1 - v1.1.3`     | `1.23, 1.22, 1.21, 1.20, 1.19` |
| `v1.1.0`              | `1.22, 1.21, 1.20, 1.19`       |

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Running an unsupported version combination of ingress-nginx and Kubernetes will lead to unintended behavior and functionality may not work as expected.

## Why does this exist? (Root Cause)

The maintainers of ingress-nginx recommend using a Kubernetes control plane version for which it is supported.

From the [documentation](https://github.com/kubernetes/ingress-nginx#supported-versions-table):  
_Supported versions for the ingress-nginx project mean that we have completed E2E tests, and they are passing for the versions listed. Ingress-Nginx versions may work on older versions but the project does not make that guarantee._

## Additional Resources

For more information see: ingress-nginx's [GitHub ReadMe](https://github.com/kubernetes/ingress-nginx#supported-versions-table)