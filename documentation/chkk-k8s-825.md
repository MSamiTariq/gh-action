---
title: Splunk OTEL Collector continuously logs errors when encountering an empty log file
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Upgrade to a Splunk OTEL Collector version that is greater than `v0.78.0`.

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

This defect may cause the collection of telemetry data to be disrupted, leading to a loss of valuable insights and monitoring capabilities. Additionally, any downstream processes or applications relying on the data collected by the Splunk OTEL Collector may be adversely affected.

## Why does this exist? (Root Cause)

[Code refactoring in upstream v0.78.0](https://github.com/open-telemetry/opentelemetry-collector-contrib/pull/21734) caused Splunk OTEL Collector to try and create create a new reader from an empty and closed file, instead of skipping it. The error is hit while trying to build the new reader, in an attempt to set the value of the offset to end of the file. This operation fails because the offsetToEnd method calls stat() on a file that is closed.

## Who is impacted and when? (Trigger Conditions)

_Affected Versions_  
All clusters using Splunk OTEL Collector version `v0.78.0` contain this Latent Availability Risk.

## Additional Resources

For more information, please refer to the following:

- [Splunk OTEL Collector Release Notes](https://github.com/signalfx/splunk-otel-collector/releases/tag/v0.78.0)
- [Upstream GitHub Issue](https://github.com/open-telemetry/opentelemetry-collector-contrib/issues/22815)
- [Upstream GitHub PR](https://github.com/open-telemetry/opentelemetry-collector-contrib/pull/22945)