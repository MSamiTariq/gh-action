---
title: Your version of Nvidia GPU Operator is no longer supported
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

We strongly recommend running a supported Nvidia GPU Operator major release as shown in the table below.

| Nvidia GPU Operator Major Version | Release Date | EOL Date   |
| :-------------------------------- | :----------- | :--------- |
| `v23.9`                           | 2023-10-23   | April 2024 |
| `v23.6`                           | 2023-07-05   | Jan 2024   |
| `v23.3`                           | 2023-04-05   | Oct 2023   |

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Running an Nvidia GPU Operator version that has reached end of support can lead to unintended behavior and functionality may not work as expected.

## Why does this exist? (Root Cause)

Every major release of the NVIDIA GPU Operator, starting with `v23.3.0`, is maintained for six months. Bug fixes and CVEs are released throughout the six months while minor feature updates are only released within the first three months.

## Additional Resources

For more details, please refer to [Official Nvidia GPU Operator Documentation](https://docs.nvidia.com/datacenter/cloud-native/gpu-operator/latest/platform-support.html#nvidia-gpu-operator-life-cycle)