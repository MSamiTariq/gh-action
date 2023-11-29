---
title: The detected Keptn Lifecycle Toolkit version is not compatible with your Kubernetes version
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Keptn Lifecycle Toolkit is only compatible with Kubernetes `v1.24` and later. Upgrade your Kubernetes version to the supported range.

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Running an unsupported version combination of Keptn Lifecycle Toolkit and Kubernetes can lead to unintended behavior and functionality may not work as expected.

## Why does this exist? (Root Cause)

Kubernetes cluster version `>= 1.24` is a prerequisite for Keptn Lifecycle Toolkit. See the doc at [this link](https://lifecycle.keptn.sh/docs/getting-started/#prerequisites).

## Additional Resources

For more information see: [Keptn Lifecycle Toolkit Prerequisites](https://lifecycle.keptn.sh/docs/getting-started/#prerequisites)