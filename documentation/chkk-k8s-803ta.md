---
title: Your Current Version of AWS Load Balancer Controller is Unsupported
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

We strongly recommend upgrading your AWS Load Balancer Controller version to the latest supported minor version: `v2.6` . You can do so by following the upgrade steps given in the official documentation [here](https://kubernetes-sigs.github.io/aws-load-balancer-controller/v2.6/deploy/installation/#create-update-strategy).

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Running a version of AWS Load Balancer Controller that has reached end of support can lead to unintended behavior and functionality may not work as expected.

## Why does this exist? (Root Cause)

As per the maintainers:

> You should use the most up to date version when possible (we maintain backwards compatibility). Currently we do support older versions (e.g. via support tickets), but we only provide security updates and bug fixes to the latest available minor versions.

## Additional Resources

Chkk is working with the upstream community for AWS Load Balancer Controller to update and streamline their support policy.