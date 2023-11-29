---
title: Fluent Bit config should support rewrite_tag filter with no Match
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Update Fluent Bit to `v1.8.11` or later.

## How to fix it, short-term workaround? (Mitigation)

Avoid specifying `rewrite_tag` with no Match in the filter parameters.

## What is the impact? (Availability Impact)

Fluent Bit will crash when a `rewrite_tag` filter with no Match is specified in the config, disrupting the process of continuous collection and aggregation of logs and data from different sources.

## Why does this exist? (Root Cause)

In Fluent Bit `v1.8.9`, a regression in the logic for applying filters was introduced where if the `rewrite_tag` parameter with no Match (e.g. when Match_Regex is in use) was used, it would cause the fluent bit to crash resulting in a SIGSEGV error.

## Who is impacted and when? (Trigger Conditions)

_Affected Versions_  
All Kubernetes clusters using the Fluent Bit versions `v1.8.9` and `v1.8.10` are affected.

_Affected Images_  
Container image tags for Fluent Bit provided by [fluent/fluent-bit](https://hub.docker.com/r/fluent/fluent-bit) on DockerHub for versions `v1.8.9` and `v1.8.10` are affected.

Container images for Fluent Bit distributed by [AWS](https://github.com/aws/aws-for-fluent-bit) with versions `v2.21.1`, `v2.21.2`, `v2.21.3`, and `v2.21.4` are affected.

## Additional Resources

The GitHub issue can be found [here](https://github.com/fluent/fluent-bit/issues/4246)