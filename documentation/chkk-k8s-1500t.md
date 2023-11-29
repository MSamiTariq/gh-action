---
title: Current version of Kubernetes is not compatible with  Prometheus Operator version
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

We strongly recommend upgrading your cluster’s Kubernetes version to a supported version (`>= v1.16`) as per the requirements of the Prometheus Operator.

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Your current version of Prometheus Operator does not support the Kubernetes version you are running, which means that the software may have incompatibilities leading to unknown behavior.

## Why does this exist? (Root Cause)

As per the [requirements](https://github.com/prometheus-operator/prometheus-operator#prerequisites) by Prometheus, version `>= 0.39.0` of the Prometheus Operator requires a Kubernetes cluster of version `>= 1.16.0`

## Additional Resources

For more information, refer to following links

- [GitHub Readme for Prometheus Operator](https://github.com/prometheus-operator/prometheus-operator#prerequisites) 
- [Prometheus Operator Documentation](https://prometheus-operator.dev/docs/operator/compatibility/#kubernetes)