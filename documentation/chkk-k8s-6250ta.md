---
title: Unsupported version of CSI Livenessprobe
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Upgrade to one of the supported version of CSI Livenessprobe which can be found [here](https://kubernetes-csi.github.io/docs/livenessprobe.html). Currently the supported versions are `v2.11`, `v2.10` and `v2.9` and `v2.8`.

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Running a CSI Livenessprobe version that has reached end of support can lead to unintended behavior and functionality may not work as expected.

## Why does this exist? (Root Cause)

An outdated version of CSI Livenessprobe will not receive security updates or technical support, and may cause your software to have incompatibilities leading to unknown behavior.

## Additional Resources

For more information, please refer to the [official documentation](https://kubernetes-csi.github.io/docs/livenessprobe.html)