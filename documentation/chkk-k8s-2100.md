---
title: Incompatible version of AWS EBS CSI Driver with Amazon EKS.
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

We strongly recommend using a [supported AWS EBS CSI Driver and Amazon EKS Kubernetes version combination.  
](https://docs.aws.amazon.com/eks/latest/userguide/managing-ebs-csi.html)

1. Find out which version of Kubernetes you are using.

```shell
aws eks describe-cluster \
    --region <REGION> \
    --name <CLUSTER_NAME> \
    --query 'cluster.version'
```

2. Find out the updated version of aws-ebs-csi-driver

```shell
aws eks describe-addon-versions \
    --addon-name aws-ebs-csi-driver \
    --kubernetes-version <K8S_VERSION> \
    --query "addons[].addonVersions[].addonVersion" \
    --output json
```

3. Update the Add-On to one of the versions returned in the output.

```shell
aws eks update-addon \
	--cluster-name my-cluster \
	--addon-name aws-ebs-csi-driver \
	--addon-version <ADDON-VERSION> \
	--resolve-conflicts PRESERVE
```

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Running an AWS EBS CSI Driver version that has not passed Amazon EKS release qualification criteria puts your cluster at the risk of running into compatibility issues.

## Why does this exist? (Root Cause)

Amazon EKS recommends and supports specific versions of AWS EBS CSI Driver for each EKS cluster version. Running unsupported versions puts your cluster at the risk of running into compatibility issues. Moreover  Amazon EKS doesn't automatically update Amazon EBS CSI for your cluster when new versions are released or after you update your cluster to a new Kubernetes minor version. To update Amazon EBS CSI on an existing cluster, you must initiate the update and then Amazon EKS updates the Add-On for you.

## Additional Resources

For more information, please refer to the official [EKS documentation](https://docs.aws.amazon.com/eks/latest/userguide/managing-ebs-csi.html).

**Note**: If you're using the self-managed AWS EBS CSI Driver, we recommend transitioning to the managed Add-On to ensure you're running the tested bits from EKS.