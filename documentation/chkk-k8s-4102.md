---
title: Karpenter's node creation logic causes consistency issues and race conditions
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Upgrade your Karpenter version to `v0.28.0` or greater.

## How to fix it, short-term workaround? (Mitigation)

As mentioned in this Github comment [here](https://github.com/aws/karpenter/issues/2734#issuecomment-1295311257), there are two possible mitigations:

1. Use instance-id hostnames in your VPC, which would result in your nodes being named after their instance-ids rather than their private IP addresses. For more information on this approach, please refer to the documentation on [Resource Naming](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-instance-naming.html).
2. Upgrade to Karpenter `v0.19.3` or greater, which added native spot termination handling via [this PR](https://github.com/aws/karpenter/pull/2546). This allowed Karpenter to catch AWS Health Events including Instance Status Events that will be used to delete nodes in the case of health check failure

## What is the impact? (Availability Impact)

Karpenter's node creation logic causes consistency issues, race conditions, leaked instances, and reduced node launch performance. This leads to resource constraints, degraded performance, orphaned nodes and instances, which can impact the availability of a Kubernetes cluster. Additionally, the reduced node launch performance can cause delays in scaling up or down the cluster, which can impact the availability of applications running on the cluster.

## Why does this exist? (Root Cause)

The problem originates from Karpenter’s method of node creation, where the node object is generated on the Kubernetes API server right after the VM instance is created. This contrasts with the expectation of Kubernetes cloud providers, who rely on the kubelet to register nodes with the API server in an asynchronous and distributed way. Consequently, this discrepancy leads to problems like inconsistent node state, slower node launches, and the potential inability to establish dynamic labels through AWS userData.

## Who is impacted and when? (Trigger Conditions)

Karpenter versions `< 0.28.0` will have this risk.

## Additional Resources

For more information, please refer to 

1. [Design doc addressing the issue](https://github.com/aws/karpenter/pull/2944)
2. [PR that fixed this issue](https://github.com/aws/karpenter/pull/3408)