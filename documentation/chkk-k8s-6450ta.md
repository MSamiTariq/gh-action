---
title: Unsupported version of Grafana
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Upgrade to one of the supported version of Grafana which currently are: `v10.2.x`, `v10.1.x` and `v9.5.x`. Refer to the [official upgrade guide](https://grafana.com/docs/grafana/latest/upgrade-guide/) for more details.

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Running a Grafana version that has reached end of support can lead to unintended behavior and functionality may not work as expected.

## Why does this exist? (Root Cause)

Grafana supports the latest 2 minor releases of the current major version and the latest minor release of the previous major version. An outdated version of Grafana will not receive security updates or technical support, and may cause your software to have incompatibilities leading to unknown behavior.

## Additional Resources

For more information, please refer to:

- [ticket outlining the official support policy](https://community.grafana.com/t/clarifications-on-grafana-release-support-lifecycle/77054/4)