---
title: Unsupported version of Cluster Autoscaler
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Upgrade to a Cluster Autoscaler version that corresponds to one of the supported versions of Kubernetes which can be found [here](https://kubernetes.io/releases/#release-history).

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Running a Cluster Autoscaler version that has reached end of support can lead to unintended behavior and functionality may not work as expected.

## Why does this exist? (Root Cause)

Cluster Autoscaler supports versions corresponding to currently supported Kubernetes versions. An outdated version of Cluster Autoscaler will not receive security updates or technical support, and may cause your software to have incompatibilities leading to unknown behavior.

## Additional Resources

For more information, please refer to:

- [the official documentation](https://github.com/kubernetes/autoscaler/blob/master/cluster-autoscaler/README.md#:~:text=Cluster%20Autoscaler%20releases%20patches%20for%20versions%20corresponding%20to%20currently%20supported%20Kubernetes%20versions)