---
title: A nil pointer dereference in aggregate filter translator causes Gloo Edge pods to restart (COPY)
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Upgrade your FluentD version to `v1.16.2` or greater.

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

If FluentD in a Kubernetes cluster runs out of memory, it can lead to log data loss and disrupt logging and monitoring functions. This memory issue may result in performance degradation and resource contention, impacting service traffic and availability within the cluster.

## Why does this exist? (Root Cause)

The abnormal elevation in FluentD’s memory usage occurs due to a continuous increase of the log cache in the _ignore repeated logs_ feature ([source](https://github.com/fluent/fluentd/blob/0a6d706a9cee5882d751b2cc6169696709df0134/lib/fluent/log.rb#L480)). Each new message, which can be both large and non-repetitive, are stored as the key within that cache. Since the memory is never released, the size of the cache grows continuously, resulting in FluentD hitting OOM issues. 

## Who is impacted and when? (Trigger Conditions)

FluentD versions `≥ 1.11.3` and versions `< v1.16.2` will have this risk.

## Additional Resources

For more information, please refer to 

1. [Github Issue](https://github.com/fluent/fluentd/issues/4174)
2. [PR that fixed this issue](https://github.com/fluent/fluentd/pull/4229/files)