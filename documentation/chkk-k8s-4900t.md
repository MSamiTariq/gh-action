---
title: The detected Jaeger Operator version is not compatible with your Kubernetes version
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Use a version of Jaeger Operator that is supported for your version of Kubernetes. Please refer to the following table for compatible versions:

| Jaeger Operator Version | Recommended Kubernetes Versions |
| :---------------------: | :-----------------------------: |
|        `v1.49.*`        |        `v1.19` to `v1.28`       |
|        `v1.48.*`        |        `v1.19` to `v1.27`       |
|        `v1.47.*`        |        `v1.19` to `v1.27`       |
|        `v1.46.*`        |        `v1.19` to `v1.26`       |
|        `v1.45.*`        |        `v1.19` to `v1.26`       |
|        `v1.44.*`        |        `v1.19` to `v1.26`       |
|        `v1.43.*`        |        `v1.19` to `v1.26`       |
|        `v1.42.*`        |        `v1.19` to `v1.26`       |
|        `v1.41.*`        |        `v1.19` to `v1.25`       |
|        `v1.40.*`        |        `v1.19` to `v1.25`       |
|        `v1.39.*`        |        `v1.19` to `v1.25`       |
|        `v1.38.*`        |        `v1.19` to `v1.25`       |
|        `v1.37.*`        |        `v1.19` to `v1.24`       |
|        `v1.36.*`        |        `v1.19` to `v1.24`       |
|        `v1.35.*`        |        `v1.19` to `v1.24`       |
|        `v1.34.*`        |        `v1.19` to `v1.24`       |
|        `v1.33.*`        |        `v1.19` to `v1.23`       |
|        `v1.32.*`        |        `v1.19` to `v1.22`       |
|        `v1.31.*`        |        `v1.19` to `v1.22`       |
|        `v1.30.*`        |        `v1.19` to `v1.22`       |

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Running an incompatible version combination of Jaeger Operator and Kubernetes will lead to unintended behavior and functionality may not work as expected.

## Why does this exist? (Root Cause)

Jaeger recommends using a Kubernetes control plane version for which Jaeger Operator is supported. See [Jaeger Operator compatibility matrix](https://github.com/jaegertracing/jaeger-operator/blob/main/COMPATIBILITY.md) 

## Additional Resources

For more information see: [Jaeger Operator compatibility matrix](https://github.com/jaegertracing/jaeger-operator/blob/main/COMPATIBILITY.md)