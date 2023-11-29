---
title: Unsupported version of CSI node-driver-registrar
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Upgrade to one of the supported version of CSI node-driver-registrar which can be found [here](https://kubernetes-csi.github.io/docs/node-driver-registrar.html). Currently the supported versions are `v2.6`, `v2.7` and `v2.8`.

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Running a CSI node-driver-registrar version that has reached end of support can lead to unintended behavior and functionality may not work as expected.

## Why does this exist? (Root Cause)

An outdated version of CSI node-driver-registrar will not receive security updates or technical support, and may cause your software to have incompatibilities leading to unknown behavior.

## Additional Resources

For more information, please refer to the [official documentation](https://kubernetes-csi.github.io/docs/node-driver-registrar.html)