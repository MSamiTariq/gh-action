---
title: Flagger is running on an incompatible version of K8s
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Upgrade K8s to `v1.16` or newer.

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Flagger is not supported by the kubernetes version you are running, which means that the software may have incompatibilities leading to unknown behavior.

## Why does this exist? (Root Cause)

Flagger official documentation requires running Flagger on kubernetes version `v1.16` or later.

## Additional Resources

For more information, you can view the documentation [here](https://docs.flagger.app/install/flagger-install-on-kubernetes#prerequisites)