---
title: Unsupported containerd version
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

We strongly recommend upgrading containerd to a supported version. The table below is taken from the [official documentation](https://containerd.io/releases/#support-horizon) can be used as a reference.

| Release | Status      | Start             | End of Life                                      |
| :------ | :---------- | :---------------- | :----------------------------------------------- |
| `v2.0`  | Next        | TBD               | TBD                                              |
| `v1.7`  | Active      | March 10, 2023    | max(March 10, 2024 or release of 2.0 + 6 months) |
| `v1.6`  | LTS         | February 15, 2022 | max(February 15, 2025 or next LTS + 6 months)    |
| `v1.5`  | End of Life | May 3, 2021       | February 28, 2023                                |

All the versions prior to the ones given in the above table have reached end of life and are not supported anymore

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Running a containerd version that has reached end of support can lead to unintended behavior and functionality may not work as expected.

## Why does this exist? (Root Cause)

containerd follows a [release cycle](https://containerd.io/releases/), after which the particular release branch is no longer supported and no new patches will be accepted.

## Additional Resources

For more details, please refer to the [official containerd documentation](https://containerd.io/releases/)