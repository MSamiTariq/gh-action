---
title: Unsupported version of Linkerd
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Upgrade to one of the supported versions of Linkerd. See the available releases at the link below: 

[Linkerd releases](https://github.com/linkerd/linkerd2/releases)

Also see Linkerd's documentation on upgrading at the link below:

[Linkerd upgrade guide](https://linkerd.io/2.13/tasks/upgrade/)

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Running an unsupported version of Linkerd will lead to unintended behavior and functionality may not work as expected.

## Why does this exist? (Root Cause)

Linkerd publishes releases into multiple channels; stable and edge. 

Stable releases are published periodically and are intended for production use. In general, only the latest major stable version is supported.

| Linkerd Release   | Status      |
| :---------------- | :---------- |
| `stable-2.14.x`   | Supported   |
| `< stable-2.14.0` | Unsupported |

Edge releases are frequent (usually, weekly) and can be used to work with the latest and experimental features. Edge releases may introduce breaking changes. There is no version support policy for edge releases, therefore it is recommended to stay on the latest edge release. If upgrades on a fast pace are not feasible, consider switching to the stable releases.

## Additional Resources

For more information see the following documentations: 

- [Linkerd: Releases and Versions](https://linkerd.io/releases/)
- [Upgrading Linkerd](https://linkerd.io/2.13/tasks/upgrade)