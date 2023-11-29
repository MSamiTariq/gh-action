---
title: Metrics Server Container reports inaccurate or outdated metrics after restart
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Please upgrade your Metrics Server version to `v0.6.2` or greater.

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

If the Metrics Server container restarts before scraping all the metrics from the nodes, some nodes or pods may not have their resource metrics reported to the Metrics API, or the metrics may be outdated or inaccurate. This can affect the performance and reliability of the cluster, as well as the user experience of monitoring the cluster.

## Why does this exist? (Root Cause)

This defect occurs because the metrics gets stuck in an infinite loop due to incorrect metrics being parsed. This prevents the container from being able to scrape metrics from all the nodes within the given maxDuration of 22.5 seconds leading to the Metrics Server container restarting, as dictated by the metrics collection code logic, to avoid deadlock.

## Who is impacted and when? (Trigger Conditions)

_Affected Versions_  
All clusters using Metrics Server versions `v0.6.1` or `v0.6.1` contain this Latent Availability Risk.

## Additional Resources

For more information, please refer to 

1. [Github Issue](https://github.com/kubernetes-sigs/metrics-server/issues/983)
2. [PR that fixed this issue](https://github.com/kubernetes-sigs/metrics-server/pull/1009)