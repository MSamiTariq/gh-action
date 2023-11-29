---
title: Unsupported version of External Secrets Operator
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Upgrade to one of the supported External Secrets Operator minor versions i.e., N or N-1. You can find more information about External Secrets Operator releases on their official [GitHub release page](https://github.com/external-secrets/external-secrets/releases). The following table shows External Secrets Operator versions along with their End of Life dates:

| ESO Version | Kubernetes Version | Release Date | End of Life    |
| :---------- | :----------------- | :----------- | :------------- |
| `v0.9.x`    | `v1.19 → v1.28`    | Jun 22, 2023 | Release of 1.1 |
| `v0.8.x`    | `v1.19 → v1.28`    | Mar 16, 2023 | Release of 1.0 |
| `v0.7.x`    | `v1.19 → v1.26`    | Dec 11, 2022 | Jun 22, 2023   |
| `v0.6.x`    | `v1.19 → v1.24`    | Oct 9, 2022  | Mar 16, 2023   |
| `v0.5.x`    | `v1.19 → v1.24`    | Apr 6, 2022  | Dec 11, 2022   |
| `v0.4.x`    | `v1.16 → v1.24`    | Feb 2, 2022  | Oct 9, 2022    |
| `v0.3.x`    | `v1.16 → v1.24`    | Jul 25, 2021 | Apr 6, 2022    |

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Running an unsupported version of External Secrets Operator will lead to unintended behavior and functionality may not work as expected.

## Why does this exist? (Root Cause)

External Secrets Operator supports only the latest two minor releases. An unsupported version of External Secrets Operator will not receive security updates, bug fixes or new features.

As per External Secrets Operator official documentation.

_We want to provide security patches and critical bug fixes in a timely manner to our users. To do so, we offer long-term support for our latest two (N, N-1) software releases._ 

## Additional Resources

For more information see the following documentation: 

- [External Secrets Operator: Stability and support](https://external-secrets.io/latest/introduction/stability-support/)