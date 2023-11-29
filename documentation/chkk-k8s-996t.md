---
title: Redis OSS crashes due to key tracking invalidations when the ​​max number of tracked keys is reached
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Upgrade your Redis version according to the following matrix in order to fix this defect:

| **Current Redis Version**    | **Redis version with fix** |
| :--------------------------- | :------------------------- |
| `>= v6.2.7` and `<= v6.2.10` | `v6.2.11` and later        |
| `>= v7.0.0` and `<= v7.0.8`  | `v7.0.9` and later         |

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Redis server will continue to accumulate invalidations in the queue, leading to potential crashes when the queue reaches a certain size. This might cause the server to fail, resulting in downtime and possible data loss.

## Why does this exist? (Root Cause)

There is a built in limit to [client side tracking keys](https://redis.io/commands/client-tracking/), which when exceeded will invalidate keys. If the limit exceeds while executing a command, the invalidations will be queued for later since the current redis client is set. This queue is never drained if a command is not executed (through call) such as a multi-exec command getting queued. This results in the Redis server crashing.

## Who is impacted and when? (Trigger Conditions)

_Affected Versions_  
All clusters using Redis OSS versions `v6.2.7` to `v6.2.10` and `v7.0.0` to `v7.0.8` contain this Latent Availability Risk.

## Additional Resources

For more information, see

- [The associated GitHub issue](https://github.com/redis/redis/issues/11715)
- [The PR that fixes this issue](https://github.com/redis/redis/pull/11814)