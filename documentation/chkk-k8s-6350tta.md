---
title: Unsupported version of Kyverno OSS
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Upgrade to one of the supported version of Kyverno OSS. Currently the supported versions are `v1.9.x`, `v1.10.x` and `v1.11.x`. Refer to the [official upgrade guide](https://kyverno.io/docs/installation/upgrading/) for more details.

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Running a Kyverno OSS version that has reached end of support can lead to unintended behavior and functionality may not work as expected.

## Why does this exist? (Root Cause)

An outdated version of Kyverno OSS will not receive security updates or technical support, and may cause your software to have incompatibilities leading to unknown behavior.

## Additional Resources

For more information, please refer to:

- [official support policy](https://kyverno.io/docs/installation/#compatibility-matrix)
- [official upgrade guide](https://kyverno.io/docs/installation/upgrading/)