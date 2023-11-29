---
title: VPC CNI versions <1.12 will not be operational with EKS 1.26 and newer
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Before you upgrade to EKS `1.26`, upgrade your Amazon VPC CNI plugin for Kubernetes to version `1.12` or later. For more information regarding upgrading your VPC CNI Add-On, please refer to the [Working with the Amazon VPC CNI plugin for Kubernetes Amazon EKS Add-On](https://docs.aws.amazon.com/eks/latest/userguide/managing-vpc-cni.html) guide on AWS.

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Earlier versions of the Amazon VPC CNI plugin for Kubernetes are liable to crash on EKS `1.26` which can lead to broken networking across the cluster.

## Why does this exist? (Root Cause)

Amazon VPC CNI versions prior to `1.12` use outdated versions of client-go and other K8s packages. These versions are not compatible with EKS `1.26`.

## Who is impacted and when? (Trigger Conditions)

_Affected Versions_  
All EKS clusters `>=v1.26.x` using Amazon VPC CNI versions `<v1.12.0` contain this Latent Availability Risk.

## Additional Resources

For more details, please see:

- [AWS’s official user guide ](https://docs.aws.amazon.com/eks/latest/userguide/kubernetes-versions.html)
- [GitHub Issue](https://github.com/aws/amazon-vpc-cni-k8s/issues/2195) created by the maintainers that highlights the outdated packages