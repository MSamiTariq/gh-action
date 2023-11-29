---
title: Unsupported version of KEDA
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Upgrade KEDA to a supported version. Currently supported versions are: `v2.12` and `v2.11`.

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Running an unsupported version of KEDA will lead to unintended behavior and functionality may not work as expected.

## Why does this exist? (Root Cause)

KEDA offers n-1 support for bug and security fixes. In other words, the current release and the previous release are supported. For example, if the latest stable KEDA release is `2.8`, then KEDA `2.8.x` and `2.7.x` are currently supported.

## Additional Resources

For more details, please refer to the following links 

- [KEDA Version Support Policy](https://github.com/kedacore/governance/blob/main/DEPRECATIONS.md#:~:text=The%20KEDA%20runtime%2C%20which%20consists%20of%20the%20operator%20and%20metric%20server%2C%20will%20provide%20support%20on%20the%20deprecated%20features%20for%206%20months%20(currently%20the%20equivalent%20of%202%20releases)%20after%20the%20deprecation%20was%20announced.%20In%20the%20following%20release%2C%20the%20feature%20will%20be%20removed.)
- [KEDA Release Roadmap and Upcoming Release Cycles](https://github.com/kedacore/keda/blob/main/ROADMAP.md)