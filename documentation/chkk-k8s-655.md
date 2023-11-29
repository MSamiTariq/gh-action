---
title: AKS versions 1.23.0 till 1.23.7 have been deprecated
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Upgrade your kubernetes version to `v1.23.8` or higher.

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

A bug in the upstream kubernetes project had been discovered in some versions before `v1.23.6` that causes pods to be in state OutOfCpu if a large number of pods are spun up in a short amount of time.

## Why does this exist? (Root Cause)

AKS deprecated kubernetes versions `v1.23.0` till `v1.23.7` due to a critical bug fix introduced in `v1.23.8`.

## Additional resources

For more details, please refer to the following links:  
[GitHub Issue](https://github.com/Azure/AKS/issues/3071)  
[GitHub Issue](https://github.com/kubernetes/kubernetes/issues/107679)