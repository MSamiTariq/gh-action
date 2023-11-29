---
title: Fluent Bit should skip non-Golang binaries when loading output plugins
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Update Fluent Bit to `v1.8.11` or later.

## How to fix it, short-term workaround? (Mitigation)

Avoid specifying a non-Golang binary in the output plugin.

## What is the impact? (Availability Impact)

Fluent Bit will crash when a non-Golang binary is accidentally provided in the output plugin, disrupting the process of continuous collection and aggregation of logs and data from different sources.

## Why does this exist? (Root Cause)

Fluent Bit currently supports integration of Golang-based plugin binaries that are built as shared objects for output plugins only.

## Who is impacted and when? (Trigger Conditions)

_Affected Versions_  
All Kubernetes clusters using the Fluent Bit earlier than `v1.8.11` are affected.

_Affected Images_  
Container image tags for Fluent Bit provided by [fluent/fluent-bit](https://hub.docker.com/r/fluent/fluent-bit) on DockerHub for versions \<`v1.8.11` are affected.

Container images for Fluent Bit distributed by [AWS](https://github.com/aws/aws-for-fluent-bit) with versions \< `v2.21.5` are affected.