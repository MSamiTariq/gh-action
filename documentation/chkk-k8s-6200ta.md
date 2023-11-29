---
title: Unsupported version of CSI external-resizer
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Upgrade to one of the supported version of CSI external-resizer which can be found [here](https://kubernetes-csi.github.io/docs/external-resizer.html). Currently the supported versions are: `v1.7`, `v1.8` and `v1.9`.

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Running a CSI external-resizer version that has reached end of support can lead to unintended behavior and functionality may not work as expected.

## Why does this exist? (Root Cause)

An outdated version of CSI external-resizer will not receive security updates or technical support, and may cause your software to have incompatibilities leading to unknown behavior.

## Additional Resources

For more information, please refer to the [official documentation](https://kubernetes-csi.github.io/docs/external-resizer.html)