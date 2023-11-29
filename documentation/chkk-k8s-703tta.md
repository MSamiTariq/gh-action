---
title: VPC CNI crashes for versions lower than v1.11.1 if ANNOTATE_POD_IP is set to true
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Update Amazon VPC CNI to `v1.11.1` or later to apply the available patch.

## How to fix it, short-term workaround? (Mitigation)

None

## What is the impact? (Availability Impact)

As soon as ANNOTATE_POD_IP is set to true on VPC CNI `v1.11.0` and below, the CNI pod goes to CrashloopBackOff, which leads to broken networking across the cluster.

## Why does this exist? (Root Cause)

In VPC CNI `v1.11.0` and below, if target pod annotations are empty, it will cause IPAMD to panic while patching the pod ip. This specific case is unhandled as the variable becomes nil instead of an empty map causing the panic.

## Who is impacted and when? (Trigger Conditions)

_Affected Versions_  
All clusters using Amazon VPC CNI `<= v1.11.0` are affected by this Latent Availability Risk.

## Additional Resources

For more details, please refer to the following [GitHub Issue](https://github.com/aws/amazon-vpc-cni-k8s/issues/1973)