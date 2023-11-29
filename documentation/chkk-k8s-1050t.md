---
title: Nil Point Deference in Thanos v0.29 causing Ruler and Query pods to fail
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Upgrade Thanos to `v0.30.2`.

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

The impact of failing query and ruler pods is as follows:

The Thanos query pods are responsible for responding to queries from users and returning the aggregated data from clusters. If the query pods fail, querying the data stored in Thanos becomes unavailable.

The Thanos ruler pods are responsible for evaluating and triggering alerts based on the data stored in Thanos. If the ruler pods fail, alerting becomes unavailable, which means that important issues may go undetected.

## Why does this exist? (Root Cause)

The nil dereference pointer exists due to a bug in code where a case was not being handled properly causing it to return a nil pointer, as mentioned [here](https://github.com/thanos-io/thanos/issues/6021#issuecomment-1398600592).

## Who is impacted and when? (Trigger Conditions)

_Affected Versions_  
All clusters using Thanos versions `>= 0.29.0` and `<v0.30.2` contain this Latent Availability Risk.

## Additional Resources

For more information, see:

1. [Github Issue](https://github.com/thanos-io/thanos/issues/6021#issuecomment-1377422043)
2. [The PR that fixed this issue](https://github.com/thanos-io/thanos/pull/6066)