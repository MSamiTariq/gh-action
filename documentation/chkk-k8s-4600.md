---
title: The detected Vitess Operator version is not compatible with your Kubernetes version
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Use a version of Vitess Operator that is supported for your version of Kubernetes. Please refer to the following table for compatible versions:

| Vitess Operator Version | Recommended Kubernetes Versions               |
| ----------------------- | --------------------------------------------- |
| `v2.0.*`                | `v1.13.*`, `v1.14.*`, or `v1.15.*`            |
| `v2.1.*`                | `v1.15.*`, `v1.16.*`, or `v1.17.*`            |
| `v2.2.*`                | `v1.15.*`, `v1.16.*`, or `v1.17.*`            |
| `v2.3.*`                | `v1.15.*`, `v1.16.*`, or `v1.17.*`            |
| `v2.4.*`                | `v1.15.*`, `v1.16.*`, or `v1.17.*`            |
| `v2.5.*`                | `v1.17.*`, `v1.18.*`, or `v1.19.*`            |
| `v2.6.*`                | `v1.20.*`, `v1.21.*`, or `v1.22.*`            |
| `v2.7.*`                | `v1.20.*`, `v1.21.*`, or `v1.22.*`            |
| `v2.8.*`                | `v1.22.*`, `v1.23.*`, or `v1.24.*`            |
| `v2.9.*`                | `v1.22.*`, `v1.23.*`, or `v1.24.*`            |
| `v2.10.*`               | `v1.22.*`, `v1.23.*`, `v1.24.*`, or `v1.25.*` |
| `v2.11.*`               | `v1.22.*`, `v1.23.*`, `v1.24.*`, or `v1.25.*` |

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Running an unsupported version combination of Vitess Operator and Kubernetes will lead to unintended behavior and functionality may not work as expected.

## Why does this exist? (Root Cause)

PlanetScale recommends using a Kubernetes control plane version for which Vitess Operator is supported. See [Vitess Operator compatibility matrix](https://github.com/planetscale/vitess-operator#compatibility) 

## Additional Resources

For more information see: [Vitess Operator compatibility matrix](https://github.com/planetscale/vitess-operator#compatibility)