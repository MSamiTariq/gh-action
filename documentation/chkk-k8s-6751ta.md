---
title: Unsupported version of Gloo Edge Enterprise
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Upgrade Gloo Edge Enterprise to a supported version. Currently supported versions are: `1.15`, `1.14`, `1.13` and `1.12`.

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Running an unsupported version of Gloo Edge Enterprise will lead to unintended behavior and functionality may not work as expected.

## Why does this exist? (Root Cause)

Gloo Edge Enterprise offers n-3 patching support for bug and critical security fixes. In other words, the current release and the three previous releases are supported. For example, if the latest stable Gloo Edge Enterprise release is `1.14`, then Gloo Edge Enterprise `1.13.x`, `1.12.x`, and `1.11.x` are also supported.

## Additional Resources

For more details, please refer to the official [Gloo Edge Enterprise documentation](https://docs.solo.io/gloo-edge/latest/reference/support/)