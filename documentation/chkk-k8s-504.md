---
title: Memory leak in Calico kube-controllers' Node controller pod
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Upgrade Calico to version `v3.25.1` or later.

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this defect.

## What is the impact? (Availability Impact)

This defect can lead to slower response times, pod crashes, and overall performance degradation in your application.

## Why does this exist? (Root Cause)

In large clusters (>20K pods), calico-kube-controllers Node controller will leak memory in its internal pod cache within the IPAM controller loop.

This defect exists due to an extremely inefficient cache refresh loop implementation that issues separate GET requests on every pod in the cluster on startup which causes an internal FIFO queue to fall far behind and start dropping delete requests on resources.

## Who is impacted and when? (Trigger Conditions)

_Affected Versions_

All clusters using Calico version earlier than `v3.25.1` contain this Latent Availability Risk.

## Additional Resources

For more information see [this GitHub PR](https://github.com/projectcalico/calico/pull/7433)