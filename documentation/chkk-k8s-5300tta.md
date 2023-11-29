---
title: Unsupported version of Tailscale
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

We strongly recommend upgrading Tailscale to the latest stable release which is `v1.54`.

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Running an Tailscale version that has reached end of support can lead to unintended behavior and functionality may not work as expected.

## Why does this exist? (Root Cause)

Tailscale follows an alternating version numbering scheme. Even numbers (1.0, 1.2, 1.4) are stable versions, and odd numbers (1.1, 1.3, 1.5) are unstable versions. The 2 latest minor releases, one stable and one unstable, are supported any given time.

For bug fixes, Tailscale delivers patches in the current stable version as well as the current (unstable) version, so that the bug fix that land in the current unstable release are also present in the next stable release.

Even though bug fixes land in both the latest stable and unstable releases, our recommendation is to use the stable release in your production environments.

See the official [Tailscale docs](https://tailscale.com/kb/1168/versions/#version-support) for more details.

## Additional Resources

For more information see

- [Tailscale's official documentation](https://tailscale.com/kb/1168/versions/#version-support)
- [Tailscale's Github Releases](https://github.com/tailscale/tailscale/releases)