---
title: Some pods may experience broken external networking while running VPC CNI versions below v1.7.2
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Upgrade Amazon VPC CNI to `v1.7.2` or later to apply the available patch. 

For more information, see the "Updating the Amazon EKS Add-On" heading AWS documentation

- [Managing the Amazon VPC CNI plugin for Kubernetes Add-On](https://docs.aws.amazon.com/eks/latest/userguide/managing-vpc-cni.html)

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation for this Availability Risk

## What is the impact? (Availability Impact)

Some pods may fail to start up correctly and be stuck in Init state. This can have a significant impact on availability, as pods may be unable to communicate with other services or resources, resulting in service disruption or downtime. The likelihood of this defect occurring increases when there are a large number of pods.

## Why does this exist? (Root Cause)

Prior to `v1.7.2`, VPC CNI relied solely on the IMDS to retrieve networking information for the EC2 instance, without validating that information with the EC2 API. This could sometimes manifest as stale or incorrect network configuration being applied to new pods, leading to connectivity issues.

## Who is impacted and when? (Trigger Conditions)

_Affected Versions_

All Kubernetes clusters using VPC CNI version earlier than `v1.7.2` contain this Latent Availability Risk.

_Affected Images_

One release may have multiple tags based on the image source. e.g. `v1.9.3`, `v1.9.3-eksbuild.1` are all affected tags for the version `v1.9.3`.

The official image name is `*.amazonaws.com/amazon-k8s-cni`.

e.g. `602401143452.dkr.ecr.us-west-2.amazonaws.com/amazon-k8s-cni:v1.10.0-eksbuild.1` is the official image provided by AWS in `us-west-2`. 

## Additional Resources

For more information see the following:

- [Github Issue](https://github.com/aws/amazon-vpc-cni-k8s/issues/1070)
- [Pull Request](https://github.com/aws/amazon-vpc-cni-k8s/pull/1177)