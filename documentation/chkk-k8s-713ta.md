---
title: Your Current Version of Cilium is unsupported
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

We strongly recommend upgrading your Cilium version to one of the three supported minor versions: `v1.14`, `v1.13`, `v1.12`. You can do so by following the upgrade steps given in the [Cilium Upgrade Guide](https://docs.cilium.io/en/stable/operations/upgrade/).

## How to fix it, short-term workaround? (Mitigation)

There is to mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Your current version of Cilium is no longer supported, which means that the software may have incompatibilities leading to unknown behaviour.

## Why does this exist? (Root Cause)

As per their documentation,

> The Cilium community maintains minor stable releases for the last three minor Cilium versions. Older Cilium stable versions from minor releases prior to that are considered EOL.

## Additional Resources

For more information, please refer to [Cilium’s Github Readme.](https://github.com/cilium/cilium#stable-releases)