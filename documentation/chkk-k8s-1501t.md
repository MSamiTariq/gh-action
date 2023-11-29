---
title: Your current version of Prometheus is outdated.
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

We strongly recommend upgrading your Prometheus version to a supported version as per the release cycle of Prometheus. The currently supported releases are Prometheus `v2.45` for LTS, and Prometheus `v2.48` for STS.

You can find more information about Prometheus releases on their official [GitHub release page](https://github.com/prometheus/prometheus/releases).

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Your current version of Prometheus is outdated, which means that the software may have incompatibilities leading to unknown behavior. 

## Why does this exist? (Root Cause)

Prometheus follows a 6 week minor release cycle. After the 6 week period, support for older releases is dropped, unless it is selected to be a Long Term Support (LTS) version. 

**List of LTS releases** 

| Release            | Release Date | End of support |
| :----------------- | :----------- | :------------- |
| Prometheus `v2.45` | 2023-06-23   | 2024-07-31     |
| Prometheus `v2.37` | 2022-07-14   | 2023-07-31     |

**(Non-Exhaustive) List of STS releases** 

| Release            | Release Date | End of support              |
| :----------------- | :----------- | :-------------------------- |
| Prometheus `v2.48` | 2023-11-16   | Release of Prometheus v2.49 |
| Prometheus `v2.47` | 2023-09-06   | 2023-11-16                  |
| Prometheus `v2.46` | 2023-07-25   | 2023-09-06                  |
| Prometheus `v2.44` | 2023-05-14   | 2023-07-25                  |
| Prometheus `v2.43` | 2023-03-21   | 2023-05-14                  |
| Prometheus `v2.42` | 2023-01-31   | 2023-03-21                  |
| Prometheus `v2.41` | 2022-12-20   | 2023-01-31                  |
| Prometheus `v2.40` | 2022-11-08   | 2022-12-20                  |
| Prometheus `v2.39` | 2022-10-05   | 2022-11-08                  |

## Additional Resources

For more information see: [Prometheus Release Cycle](https://prometheus.io/docs/introduction/release-cycle/#long-term-support).