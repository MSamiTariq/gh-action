---
title: Unsupported version of AKS
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Update to one of the supported AKS versions as shown in the table below.

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Using a Kubernetes version that is no longer supported by AKS will lead to compatibility issues, and missing updates, risking the stability and functionality of your cluster.

## Why does this exist? (Root Cause)

AKS recommends using one of their officially supported Kubernetes versions. You can find the AKS Kubernetes release calendar below:

| k8s version | Upstream release | AKS preview | AKS GA   | End of life |
| :---------- | :--------------- | :---------- | :------- | :---------- |
| `v1.21`     | Apr-08-21        | May 2021    | Jul 2021 | Jul 2022    |
| `v1.22`     | Aug-04-21        | Sept 2021   | Dec 2021 | Dec 2022    |
| `v1.23`     | Dec 2021         | Jan 2022    | Apr 2022 | Apr 2023    |
| `v1.24`     | Apr-22-22        | May 2022    | Jul 2022 | Jul 2023    |
| `v1.25`     | Aug 2022         | Oct 2022    | Dec 2022 | Jan 2024    |
| `v1.26`     | Dec 2022         | Feb 2023    | Apr 2023 | Mar 2024    |
| `v1.27`     | Apr 2023         | Jun 2023    | Jul 2023 | Jul 2024    |
| `v1.28`     | Aug 2023         | Aug 2023    | Sep 2023 |             |

## Additional resources

For more details, please refer to the official [AKS documentation](https://learn.microsoft.com/en-us/azure/aks/supported-kubernetes-versions?tabs=azure-cli)