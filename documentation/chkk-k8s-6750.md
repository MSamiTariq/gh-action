---
title: A nil pointer dereference in aggregate filter translator causes Gloo Edge pods to restart
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Upgrade Gloo Edge to `v1.14.10` or greater.

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

The presence of this defect in your cluster can result in service disruptions, as requests may not reach their desired destination. It can also lead to unpredictable network behavior, characterized by misrouting, incorrect processing, and request drops, ultimately resulting in outages and potential downtime.

## Why does this exist? (Root Cause)

The root cause of this issue is the absence of proper object instantiation within the aggregate filter translator code. This oversight prevents the creation of essential report objects for TCP listeners, resulting in a panic and subsequent crashes when handling TCP traffic.

## Who is impacted and when? (Trigger Conditions)

Gloo Edge versions `≥ 1.11.17` and `< 1.14.10` will have this risk.

## Additional Resources

For more information, please refer to 

1. [Github Issue](https://github.com/solo-io/gloo/issues/8405)
2. [PR that fixed this issue](https://github.com/solo-io/gloo/pull/8407)