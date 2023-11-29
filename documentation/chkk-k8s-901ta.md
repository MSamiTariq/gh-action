---
title: Fluent Bit should not pause data ingestion when filesystem storage is enabled
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Upgrade Fluent Bit to `v1.8.11` or later.

## How to fix it, short-term workaround? (Mitigation)

Avoid specifying a filesystem storage type as input.

## What is the impact? (Availability Impact)

Fluent Bit will stop data ingestion disrupting process of continuous collection and aggregation of logs and data from different sources. This will result in incomplete information being received at target ends.

## Why does this exist? (Root Cause)

In Fluent Bit `v1.8.7`, a regression in the logic for handling data chunks was introduced where if the filesystem storage type was enabled in the input, it would pause the data ingestion.

## Who is impacted and when? (Trigger Conditions)

_Affected Versions_  
All Kubernetes clusters using the Fluent Bit versions `v1.8.7`, `v1.8.8`, `v1.8.9` and `v1.8.10` are affected.

_Affected Images_  
Container image tags for Fluent Bit provided by [fluent/fluent-bit](https://hub.docker.com/r/fluent/fluent-bit) on DockerHub for versions `v1.8.7`, `v1.8.8`, `v1.8.9` and `v1.8.19` are affected.

Container images for Fluent Bit distributed by [AWS](https://github.com/aws/aws-for-fluent-bit) with versions `v2.20.0`, `v2.21.0`, `v2.21.1`, `v2.21.2`, `v2.21.3` and `v2.21.4` are affected.

## Additional Resources

The GitHub issue can be found [here](https://github.com/fluent/fluent-bit/issues/4221)