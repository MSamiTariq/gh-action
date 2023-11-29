---
title: Unsupported version of Flux CD (source controller)
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

We strongly recommend upgrading Flux CD (source controller) to one of the currently supported versions. Flux CD releases corresponding to the `source controller` versions  `v0.36`, `v1.0` and `v1.1` are currently supported. Refer to the [official upgrade guide](https://fluxcd.io/flux/installation/upgrade/) for more details on how to upgrade.

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Running a Flux CD (source controller) version that has reached end of support can lead to unintended behavior and functionality may not work as expected.

## Why does this exist? (Root Cause)

Flux CD (source controller) supports the 3 latest minor releases and its corresponding controller versions. An outdated version of Flux CD (source controller) will not receive security updates or technical support, and may cause your software to have incompatibilities leading to unknown behavior.

The following table shows Flux CD versions and their corresponding source controller versions:

| Flux CD version | source controller version |
| --------------- | ------------------------- |
| 2.1             | 1.1                       |
| 2.0             | 1.0                       |
| 0.41            | 0.36                      |
| 0.40            | 0.35                      |
| 0.39            | 0.34                      |
| 0.38            | 0.33                      |
| 0.37            | 0.32                      |
| 0.36            | 0.31                      |
| 0.35            | 0.30                      |
| 0.34            | 0.29                      |
| 0.33            | 0.27, 0.28                |
| 0.32            | 0.26                      |

## Additional Resources

For more details, please refer to the:

- [Official documentation outlining supported releases](https://fluxcd.io/flux/releases/#supported-releases)
- [Official documentation outlining release versioning](https://fluxcd.io/flux/releases/#supported-releases)
- [official upgrade guide](https://fluxcd.io/flux/installation/upgrade/)