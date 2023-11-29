---
title: Unsupported version of Sealed Secrets Controller
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Upgrade to the latest supported minor version of Sealed Secrets Controller which can be found [here](https://github.com/bitnami-labs/sealed-secrets/releases). Currently it is `v0.24`

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Running a Sealed Secrets Controller version that has reached end of support can lead to unintended behavior and functionality may not work as expected.

## Why does this exist? (Root Cause)

Sealed Secrets Controller supports only the latest release at any given time. An outdated version of Sealed Secrets Controller will not receive security updates or technical support, and may cause your software to have incompatibilities leading to unknown behavior.

## Additional Resources

For more information, please refer to the [GitHub Readme](https://github.com/bitnami-labs/sealed-secrets#supported-versions)