---
title: Unsupported version of Istio
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

We strongly recommend to use an Istio version that has not reached End of Life yet.

| Istio Version      | Release Date      | End of Life Date      |
| :----------------- | :---------------- | :-------------------- |
| `v1.20`            | Nov 14, 2023      | ~July 2024 (Expected) |
| `v1.19`            | Sep 5, 2023       | ~Mar 2024 (Expected)  |
| `v1.18`            | Jun 3, 2023       | ~Dec 2023 (Expected)  |
| `v1.17`            | February 14, 2023 | Oct 27, 2023          |
| `v1.16`            | November 15, 2022 | Jul 25, 2023          |
| `v1.15`            | August 31, 2022   | Apr 4, 2023           |
| `v1.14`            | May 24, 2022      | Dec 27, 2022          |
| `v1.13`            | February 11, 2022 | Oct 12, 2022          |
| `v1.12`            | November 18, 2021 | Jul 12, 2022          |
| `v1.11`            | August 12, 2021   | Mar 25, 2022          |
| `v1.10`            | May 18, 2021      | Jan 7, 2022           |
| `v1.9`             | February 9, 2021  | Oct 8, 2021           |
| `v1.8`             | November 10, 2020 | May 12, 2021          |
| `v1.7`             | August 21, 2020   | Feb 25, 2021          |
| `v1.6` and earlier |                   |                       |

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Running an unsupported version of Istio will lead to unintended behavior and functionality may not work as expected. 

## Why does this exist? (Root Cause)

Istio supports ~2 minor versions at a time and recommends using those versions that are currently in support.

## Additional Resources

For more details, please refer to the official [Istio Releases documentation](https://istio.io/latest/docs/releases/supported-releases/)