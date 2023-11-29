---
title: Incompatible version of VPC CNI with Amazon EKS
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Update your [VPC CNI Add-On version to one of the supported versions](https://docs.aws.amazon.com/eks/latest/userguide/managing-vpc-cni.html).

1. Find out which version of Kubernetes you are using.

```shell
aws eks describe-cluster \
    --region <REGION> \
    --name <CLUSTER_NAME> \
    --query 'cluster.version'
```

2. Find the updated version of `vpc-cni` for your Kubernetes version

```shell
aws eks describe-addon-versions \
    --addon-name vpc-cni \
    --region <region> \
    --kubernetes-version <K8S_VERSION> \
    --query "addons[].addonVersions[].[addonVersion, compatibilities[].defaultVersion]" \
    --output text
```

3. Update the `vpc-cni` Add-On

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Running a VPC CNI version that has not passed Amazon EKS release qualification criteria puts your cluster at the risk of running into compatibility issues. 

## Why does this exist? (Root Cause)

Amazon EKS recommends and supports specific versions of VPC CNI for each EKS cluster version. Running unsupported versions puts your cluster at the risk of running VPC CNI that has not passed Amazon EKS release qualification and compatibility criteria. More information can be found [here](https://docs.aws.amazon.com/eks/latest/userguide/managing-vpc-cni.html) 

## Additional Resources

For more details, please refer to [VPC CNI official documentation](https://docs.aws.amazon.com/eks/latest/userguide/managing-vpc-cni.html).

If you're using the self-managed VPC CNI, you can ignore this risk. However, we recommend transitioning to the managed Add-On to ensure you're running the tested bits from EKS.