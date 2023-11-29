---
title: Karpenter versions less than v0.19.3 are unable to watch namespaces by default
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Manually modify Karpenter's RBAC to list namespaces at the cluster scope or upgrade Karpenter to `v0.19.3` or later.

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Failure to grant appropriate permissions to Karpenter versions lower than `v0.19.3` may result in namespace monitoring errors and degraded performance, leading to potential disruptions in resource allocation and utilization.

## Why does this exist? (Root Cause)

Karpenter versions prior to `v0.19.3` do not handle topology spreads with namespace selectors.

## Who is impacted and when? (Trigger Conditions)

_Affected Versions_  
All clusters using Karpenter versions `< v0.19.3` contain this Latent Availability Risk.

## Additional Resources

For more information see:

- [GitHub issue](https://github.com/aws/karpenter/issues/2702)
- [GitHub PR](https://github.com/aws/karpenter/pull/2709)
- [Karpenter Upgrade Guide](https://karpenter.sh/preview/upgrade-guide/)