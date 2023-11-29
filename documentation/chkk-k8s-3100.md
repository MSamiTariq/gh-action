---
title: Data race in Prometheus Blackbox Exporter v0.21.0
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Upgrade Prometheus Blackbox Exporter to a version `> v0.21.0`. 

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

The data race in Prometheus Blackbox Exporter `v0.21.0` may lead to crashes and undefined behavior. 

## Why does this exist? (Root Cause)

In Prometheus Blackbox Exporter `v0.21.0`, a `cases.Caser` object is reused. These objects are stateful and should not be shared among goroutines. This might happen when Prometheus tries to scrape multiple targets at the same time.

## Who is impacted and when? (Trigger Conditions)

_Affected Versions_  
All clusters using Prometheus Blackbox Exporter version `0.21.0` contain this Latent Availability Risk.

## Additional resources

For more information see

- [The associated GitHub Issue](https://github.com/prometheus/blackbox_exporter/issues/922)
- [The PR that fixes this Issue](https://github.com/prometheus/blackbox_exporter/pull/927)
- [Prometheus Blackbox Exporter Releases](https://github.com/prometheus/blackbox_exporter/releases)