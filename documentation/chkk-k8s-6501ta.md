---
title: Your Current Version of Bottlerocket Update Operator is Unsupported
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

We strongly recommend upgrading your Bottlerocket Update Operator (Brupop) version to the currently supported minor version: `v1.3` . 

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Running a Brupop version that has reached end of support can lead to unintended behavior and functionality may not work as expected.

## Why does this exist? (Root Cause)

As given in their documentation:

> As per our policy, Brupop follows the semantic versioning (semver) principles, ensuring that any updates in minor versions do not introduce any breaking or backward-incompatible changes. However, please note that we only provide security patches for the latest minor version. Therefore, it is highly recommended to always keep your Brupop installation up to date with the latest available version.

## Additional Resources

For more information, please refer to [Bottlerocket's Github README](https://github.com/bottlerocket-os/bottlerocket-update-operator#version-support-policy)