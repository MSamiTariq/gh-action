---
title: Host update failures in Bottlerocket Update Operator may cause the agent to go into CrashLoopBackOff
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term  fix? (Remediation)

Update your version of Bottle Rocket Update Operator (Brupop) to `v1.3.0`

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Failure to update the hosts across nodes can expose the Kubernetes cluster to security risks, disrupt traffic, and affect service availability due to potential compatibility and stability issues.

## Why does this exist? (Root Cause)

Brupop's update delays were primarily caused by its frequent update requests and overly rapid API calls. This behavior led to conflicts with the apiserver's lock, even when updates were completed successfully.

## Who is impacted and when? (Trigger Conditions)

Brupop versions `≥ 1.0.0` and versions `< v1.3.0` will have this risk.

## Additional Resources

For more information, please refer to 

1. [Github Issue](https://github.com/bottlerocket-os/bottlerocket-update-operator/issues/483)
2. [PR that fixed this issue](https://github.com/bottlerocket-os/bottlerocket-update-operator/pull/496)