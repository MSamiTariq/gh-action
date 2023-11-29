---
title: Unsupported cert-manager version
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Upgrade cert-manager to one of the supported versions as shown in the table.

| Release | Release Date | End-of-Life     | Supported Kubernetes Version |
| :------ | :----------- | :-------------- | :--------------------------- |
| `v1.13` | Sep 12, 2023 | Release of 1.15 | `v1.23` → `v1.28`            |
| `v1.12` | May 19, 2023 | Release of 1.14 | `v1.22` → `v1.27`            |

It is recommended to upgrade one minor version at a time. See the [cert-manager upgrade guide](https://cert-manager.io/docs/installation/upgrading/).

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Running an unsupported version of cert-manager can lead to unintended behavior and functionality may not work as expected.

## Why does this exist? (Root Cause)

cert-manager recommends and supports the latest two minor versions of the cert-manager Add-On.

## Additional Resources

Refer to the following link to see the currently supported and upcoming releases 

- [cert-manager releases](https://cert-manager.io/docs/installation/supported-releases/)