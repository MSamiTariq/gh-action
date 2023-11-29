---
title: Incompatible version of Kubernetes with TDengine
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Upgrade your Kubernetes version to `v1.19.0` or higher.

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What Rs the impact? (Availability Impact)

Running TDengine on an incompatible version of Kubernetes will lead to an unintended behavior and functionality may not work as expected.

## Why does this exist? (Root Cause)

Incompatibility can exist between Add-On versions and Kubernetes versions due to changes and updates in the Kubernetes API or functionality.

## Additional Resources

For more details, please refer to [Official TDEngine Documentation](https://docs.tdengine.com/deployment/k8s/)