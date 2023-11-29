---
title: Your Current Version of Teleport is Unsupported
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

We strongly recommend upgrading your Teleport version to one of the supported major versions as defined in the table below. 

| Release | Release Date       | EOL            |
| ------- | ------------------ | -------------- |
| `v14.x` | September 20, 2023 | September 2024 |
| `v13.x` | May 8, 2023        | May 2024       |
| `v12.x` | February 6, 2023   | February 2024  |

You can do so by following the upgrade steps given in the official [Teleport Upgrade Guide](https://goteleport.com/docs/management/operations/upgrading/#upgrade-sequence)

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Running a Teleport version that has reached end of support can lead to unintended behavior and functionality may not work as expected.

## Why does this exist? (Root Cause)

Teleport provides security-critical support for the current and two previous releases. As per their release cadence, this means that a release is usually supported for 9 months.

## Additional Resources

For more information, please refer to the [Official Teleport Documentation](https://goteleport.com/docs/faq/#supported-versions)