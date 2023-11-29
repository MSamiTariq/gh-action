---
title: Your current version of Ingress NGINX Controller is unsupported
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

We strongly recommend upgrading your Ingress NGINX Controller version to one of the supported versions:

| Supported Version | Release Date |
| :---------------- | :----------- |
| `v1.9.4`          | 2023-10-25   |
| `v1.9.3`          |  2023-10-12  |
| `v1.9.1`          | 2023-10-03   |
| `v1.9.0`          | 2023-09-23   |
| `v1.8.4`          | 2023-10-12   |
| `v1.8.2`          | 2023-09-09   |
| `v1.8.1`          | 2023-07-05   |
| `v1.8.0`          | 2023-05-30   |
| `v1.7.1`          | 2023-05-05   |
| `v1.7.0`          | 2023-03-24   |
| `v1.6.4`          | 2023-02-15   |

Refer to the official [upgrade guide](https://kubernetes.github.io/ingress-nginx/deploy/upgrade/) for detailed steps.

## How to fix it, short-term workaround? (Mitigation)

There is to mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Your current version of Ingress NGINX Controller is no longer supported, which means that the software may have incompatibilities leading to unknown behaviour.

## Why does this exist? (Root Cause)

As per their release notes:

> We are dropping support for the legacy edition, that means all version `< v1.0.0` of the ingress-nginx-controller.

## Additional Resources

For more information, please refer to [NGINX Ingress Controller's support matrix](https://github.com/kubernetes/ingress-nginx#supported-versions-table)