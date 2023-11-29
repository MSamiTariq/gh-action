---
title: AWS EKS VPC CNI Pods get stuck in creation state for two minutes due to delay in adding ENI to datastore
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Update Amazon VPC CNI to `v1.11.4` or later to apply the available patch.

For more information, see the "Updating the Amazon EKS Add-On" heading AWS documentation

- [Managing the Amazon VPC CNI plugin for Kubernetes Add-On](https://docs.aws.amazon.com/eks/latest/userguide/managing-vpc-cni.html)

## How to fix it, short-term workaround? (Mitigation)

Set WARM_IP_TARGET or MINIMUM_IP_TARGET to less than the maximum IP

## What is the impact? (Availability Impact)

Pods get stuck in creation state and are unable to receive any traffic for two minutes, if WARM_IP_TARGET or MINIMUM_IP_TARGET is greater than the maximum IPs per ENI.

## Why does this exist? (Root Cause)

Pods are not started until ENI and IPs are added into IMDS. While waiting for the IPs to be present in IMDS, the logic checks if the requested CIDRS (MINIMUM_IP_TARGET) are available but if MINIMUM_IP_TARGET is more than what ENI can support, the code goes into a retry loop, hence causing a 2 minutes delay.

## Who is impacted and when? (Trigger Conditions)

_Affected Versions_

All Kubernetes clusters using VPC CNI version greater than `v1.7.4` and versions earlier than `v1.11.4` contain this Latent Availability Risk.

_Affected Images_

One release may have multiple tags based on the image source. e.g. `v1.9.3`, `v1.9.3-eksbuild.1` are all affected tags for the version `v1.9.3`.

The official image name is \*.amazonaws.com/amazon-k8s-cni.

e.g. `602401143452.dkr.ecr.us-west-2.amazonaws.com/amazon-k8s-cni:v1.11.4-eksbuild.1` is the official image provided by AWS in `us-west-2`. 

## Additional Resources

For more information see the following:

- [Github Issue](https://github.com/aws/amazon-vpc-cni-k8s/issues/1872)
- [Pull Request](https://github.com/aws/amazon-vpc-cni-k8s/pull/1975)