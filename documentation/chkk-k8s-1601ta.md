---
title: Your current version of Jenkins is unsupported
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

We strongly recommend upgrading your Jenkins version to the latest weekly or LTS release. See the following tables for the currently supported releases

| Jenkins Release | Release Date |
| :-------------- | :----------- |
| `v2.432` (STS)  | 2023-11-14   |
| `v2.426` (LTS)  | 2023-10-03   |

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Your current version of Jenkins is no longer supported, which means that the software may have incompatibilities leading to unknown behavior.

## Why does this exist? (Root Cause)

Jenkins follows a weekly minor release schedule. Security/bug fixes and new features are not backported to earlier versions, unless it's an LTS version. The following table demonstrates release dates within the 12 week cycle:

| Week               | 0   | 2      | 4   | 6      | 8   | 10       | 12  | 14     | 16  | 18     | 20  | 22       | 24  |
| :----------------- | :-- | :----- | :-- | :----- | :-- | :------- | :-- | :----- | :-- | :----- | :-- | :------- | :-- |
| Release            | W.3 | X.1 RC | X.1 | X.2 RC | X.2 | X.3 RC   | X.3 | Y.1 RC | Y.1 | Y.2 RC | Y.2 | Y.3 RC   | Y.3 |
| Baseline Selection |     |        |     |        |     | Y chosen |     |        |     |        |     | Z chosen |     |

There is a two week period for backporting followed by two weeks for testing the release candidate resulting in the release of X.1. Backporting and RC testing is repeated twice, producing X.2 and X.3. This concludes the cycle for a given baseline and the new one is started immediately based on the new baseline selected in week 10.

## Additional Resources

For more information see: [Jenkins Release Cycle](https://www.jenkins.io/download/lts/).