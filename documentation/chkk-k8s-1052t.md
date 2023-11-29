---
title: Thanos Receivers panic when querying uninitialized TSDBs
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Upgrade your Thanos version to `v0.31.0` or greater.

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

This defect can cause Thanos Receivers to panic and restart unexpectedly several times which can potentially lead to data loss, delayed monitoring data ingestion, and accuracy issues in alerting and reporting. 

## Why does this exist? (Root Cause)

As explained within the PR linked below, Thanos Receivers currently panic when retrieving labels for a TSDB (Time Series Database - used by Prometheus to store metrics) that is being initialized. The reason for this is that the tenant is added to the tenants map and the TSDB is started in the background. When retrieving labels, the MultiTSDB creates Clients for each TSDB, even if a TSDB is not yet ready.

## Who is impacted and when? (Trigger Conditions)

Thanos versions `≥ v0.29.0` and versions `< v0.31.0` will have this risk.

## Additional Resources

For more information, please refer to 

1. [Github Issue](https://github.com/thanos-io/thanos/issues/6047)
2. [PR that fixed this issue](https://github.com/thanos-io/thanos/pull/6067/files)