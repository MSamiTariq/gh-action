---
title: Apache Flink is running on an incompatible version of K8s
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

We strongly recommend installing Apache Flink on a cluster running a compatible Kubernetes version. 

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Apache Flink does not support the Kubernetes version you are running, which means that the software may have incompatibilities leading to unknown behavior.

## Why does this exist? (Root Cause)

According to the documentation, Kubernetes `v1.9` or greater is considered as a pre-requisite for Apache Flink to be installed on a cluster.

## Additional Resources

For more details, please refer to [Official Apache Flink Documentation](https://nightlies.apache.org/flink/flink-docs-master/docs/deployment/resource-providers/native_kubernetes/)