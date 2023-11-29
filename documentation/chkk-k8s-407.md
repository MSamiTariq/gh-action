---
title: CoreDNS cache plugin with serve_stale and prefetch enabled can cause race condition errors
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Upgrade CoreDNS `v1.8.1` or above.

More information on the `cache` plugin and its additional options are documented [here](https://coredns.io/plugins/cache/)

## How to fix it, short-term workaround? (Mitigation)

- Upgrade CoreDNS to `v1.8.1` or above
- Remove the `prefetch` configuration option from the `cache` plugin

## What is the impact? (Availability Impact)

With `serve_stale` and `prefetch` enabled for the `cache` plugin, there is a possibility of running into a race condition. This can cause the CoreDNS instance to panic and exit, resulting in name resolution errors and possible downtime.

## Why does this exist? (Root Cause)

CoreDNS `cache` plugin with `serve_stale` and `prefetch` enabled can cause race condition errors and subsequent exit of the CoreDNS instance.

## Who is impacted and when? (Trigger Conditions)

_Affected Versions_  
All Kubernetes cluster using CoreDNS `v1.8.0` and below as a DNS.

_Affected Images_  
Container images for CoreDNS `v1.8.0` and below are affected.