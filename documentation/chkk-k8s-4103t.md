---
title: Inefficient EC2 instance allocation strategy in Karpenter leading to overprovisioning
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Upgrade your Karpenter version to `v0.19.0` or greater.

## How to fix it, short-term workaround? (Mitigation)

No mitigation is available for this Availability Risk

## What is the impact? (Availability Impact)

Karpenter's allocation strategy in versions below `v0.19.0` leads to EC2 over-provisioning, driving inefficiencies and higher costs. This causes unnecessary spending and possible performance drawbacks.

## Why does this exist? (Root Cause)

The core of the issue stems from Karpenter's spot allocation strategy, which doesn't sufficiently prioritise cost-effectiveness. Rather than employing a capacity-optimized method grounded in pricing data, it leans on spot pool depth.

## Who is impacted and when? (Trigger Conditions)

_Affected Versions_  
All clusters using Karpenter `<v0.19.0` are affected by this Latent Availability Risk.

## Additional Resources

- [GitHub issue](https://github.com/aws/karpenter/issues/2942)
- [GitHub PR that fixes the issue](https://github.com/aws/karpenter/pull/2835)
- [Karpenter Upgrade Guide](https://github.com/aws/karpenter-core/pull/334/files)

[Capacity optimized allocation strategy for provisioning Amazon EC2 Spot](https://aws.amazon.com/about-aws/whats-new/2022/11/amazon-ec2-price-capacity-optimized-allocation-strategy-provisioning-ec2-spot-instances/)