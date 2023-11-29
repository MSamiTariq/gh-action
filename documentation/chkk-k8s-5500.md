---
title: The detected Apache Spark version is not compatible with your Kubernetes version
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Use a version of Apache Spark that is supported for your Kubernetes version. The table below can be used as a reference.

| Apache Spark Version | Supported Kubernetes Version |
| :------------------: | :--------------------------: |
|       `v3.5.0`       |          >= `v1.24`          |
|  `v3.4.0` - `v3.4.1` |          >= `v1.22`          |
|  `v3.3.3` - `v3.2.2` |          >= `v1.20`          |
| `v3.2.1` and earlier |           >= `v1.6`          |

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Running an unsupported version combination of Apache Spark and Kubernetes can lead to unintended behavior and functionality may not work as expected.

## Why does this exist? (Root Cause)

Apache recommends using a supported version of Kubernetes control plane.

## Additional Resources

For more information see: [Apache Spark Documentation](https://spark.apache.org/documentation.html)