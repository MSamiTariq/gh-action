---
title: Your Current Version of Rancher is Unsupported
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

We strongly recommend upgrading your Rancher version to one of the supported minor versions as shown in the table below:

| Version  | Release Date | End of Maintenance | End of Life   |
| -------- | ------------ | ------------------ | ------------- |
| `v2.7.x` | 16 Nov 2022  | 15 May 2024        | 18 Nov 2024   |
| `v2.6.x` | 31 Aug 2021  | 01 Mar 2023        | 30 April 2024 |
| `v2.5.x` | 06 Oct 2020  | 05 Jan 2022        | 31 Jan 2023   |
| `v2.4.x` | 30 Mar 2020  | 30 Jul 2021        | 31 Mar 2022   |
| `v2.3.x` | 08 Oct 2019  | 07 Oct 2020        | 07 Apr 2021   |
| `v2.2.x` | 16 Apr 2019  | 15 Apr 2020        | 15 Oct 2020   |
| `v2.1.x` | 19 Oct 2018  | 19 Oct 2019        | 19 Apr 2020   |
| `v2.0.x` | 01 May 2018  | 01 May 2019        | 01 Nov 2019   |
| `v1.6.x` | 08 Jun 2017  | 31 Dec 2019        | 30 Jun 2020   |

You can do so by following the upgrade steps given in the [official Rancher Upgrade Guide](https://ranchermanager.docs.rancher.com/getting-started/installation-and-upgrade/install-upgrade-on-a-kubernetes-cluster/upgrades).

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Running a Rancher version that has reached end of life can lead to unintended behavior and functionality may not work as expected.

## Why does this exist? (Root Cause)

As per their documentation, Rancher supports and provides critical bug and security fixes for approx. two to two and a half years from the release of a minor version.

## Additional Resources

For more information, please refer to [SUSE Official Documentation for Rancher](https://www.suse.com/lifecycle/#rancher).