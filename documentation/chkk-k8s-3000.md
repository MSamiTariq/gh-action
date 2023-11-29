---
title: Amazon Elastic Block Store (EBS) CSI driver is required to be installed on an EKS cluster using Amazon EBS volumes in order to upgrade the cluster to v1.23.
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Install Amazon EBS CSI driver `v1.11.4` or newer either as an [Amazon EKS Add-On](https://docs.aws.amazon.com/eks/latest/userguide/managing-ebs-csi.html) or as a [self-managed Add-On](https://github.com/kubernetes-sigs/aws-ebs-csi-driver#amazon-elastic-block-store-ebs-csi-driver).

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

If the Amazon EBS CSI driver is not installed on an EKS cluster before upgrading it to Kubernetes `v1.23`, interruptions to your workloads might occur.

## Why does this exist? (Root Cause)

From Kubernetes `v1.23`, the Kubernetes in-tree to Container Storage Interface (CSI) Volume migration feature is enabled. This feature enables the replacement of existing Kubernetes in-tree storage plugins for Amazon EBS with a corresponding Amazon EBS CSI driver.

## Additional Resources

For more details, please refer to [Amazon EKS Kubernetes Release Notes](https://docs.aws.amazon.com/eks/latest/userguide/kubernetes-version-standard.html)