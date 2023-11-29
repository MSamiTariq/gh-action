---
title: Incompatible version of kube-proxy with Amazon EKS
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Update your `kube-proxy` Add-On version to one of the [supported versions](https://docs.aws.amazon.com/eks/latest/userguide/managing-kube-proxy.html).

1. Find out which version of Kubernetes you are using.

```shell
aws eks describe-cluster \
    --region <REGION> \
    --name <CLUSTER_NAME> \
    --query 'cluster.version'
```

Find the updated version of `kube-proxy` for your Kubernetes version

```shell
aws eks describe-addon-versions \
    --addon-name kube-proxy \
    --kubernetes-version <K8S_VERSION> \
    --query "addons[].addonVersions[].[addonVersion, compatibilities[].defaultVersion]" \
    --output text
```

3. Update the `kube-proxy` Add-On

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Running a `kube-proxy` version that has not passed Amazon EKS release qualification criteria puts your cluster at the risk of running into compatibility issues. 

## Why does this exist? (Root Cause)

Amazon EKS recommends and supports specific versions of `kube-proxy` for each EKS cluster version. Running unsupported versions puts your cluster at the risk of running `kube-proxy` that has not passed Amazon EKS release qualification and compatibility criteria. More information can be found [here](https://docs.aws.amazon.com/eks/latest/userguide/managing-kube-proxy.html).

While you're upgrading, a version skew of N-3 is supported between the kubelet and kube-apiserver. Outside of that, it is recommended to use the same minor versions of Kubernetes for the two components.

## Additional Resources

For more details, please refer to [kube-proxy official documentation](https://docs.aws.amazon.com/eks/latest/userguide/managing-kube-proxy.html).