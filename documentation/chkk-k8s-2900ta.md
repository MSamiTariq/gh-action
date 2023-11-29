---
title: Unsupported version of Argo Events
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Upgrade to one of the supported versions of Argo Events which are: `v1.8.x` and `v1.7.x`. You can find more information about Argo Events [here](https://github.com/argoproj/argo-events/releases).

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Running an unsupported version of Argo Events will lead to unintended behavior and functionality may not work as expected.

## Why does this exist? (Root Cause)

Argo Events maintains release branches for the most recent two minor releases.

| Argo Events Version | Status      |
| :------------------ | :---------- |
| `v1.8.x`            | Supported   |
| `v1.7.x`            | Supported   |
| `< v1.7.0`          | Unsupported |

## Additional resources

For more information see the following documentation: 

- [Argo Events: Supported Versions](https://argoproj.github.io/argo-events/releases/#supported-versions)