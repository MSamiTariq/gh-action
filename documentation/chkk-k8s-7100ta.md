---
title: Unsupported version of CSI external-attacher
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Upgrade your CSI external-attacher to one of the supported versions which currently are: `v4.4`,`v4.3`, `v4.2`, `v4.1` and `v4.0`.

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Running a CSI external-attacher version that has reached end of support can lead to unintended behavior and functionality may not work as expected.

## Why does this exist? (Root Cause)

An outdated version of CSI external-attacher will not receive security updates or technical support, and may cause your software to have incompatibilities leading to unknown behavior.

## Additional Resources

For more information, please refer to:

- [Official support matrix](https://kubernetes-csi.github.io/docs/external-attacher.html)