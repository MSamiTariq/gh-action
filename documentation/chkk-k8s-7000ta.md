---
title: Unsupported version of Dynatrace Operator
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Upgrade Dynatrace Operator to a supported version. Currently, all versions >= `v0.6.0` are supported. Refer to the [official upgrade guide](https://www.dynatrace.com/support/help/setup-and-configuration/setup-on-k8s/guides/operation/update-uninstall-operator)for information regarding how to upgrade Dynatrace Operator.

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Running an unsupported version of Dynatrace Operator will lead to unintended behavior and functionality may not work as expected.

## Why does this exist? (Root Cause)

An outdated version of Dynatrace Operator will not receive security updates or technical support, and may cause your software to have incompatibilities leading to unknown behavior.

## Additional Resources

For more details, please refer to the following links 

- [Dynatrace Operator EOL](https://www.dynatrace.com/support/help/whats-new/end-of-support-news#dto)