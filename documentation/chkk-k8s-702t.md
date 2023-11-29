---
title: AWS EKS VPC CNI should use IMDSv2 token when fetching node IP
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Update Amazon VPC CNI to `v1.10.0` or later to apply the available patch.

```yaml k8s manifest
# Update the image for both main container and init container tag in your VPC CNI k8s manifest
  containers:
    - name: aws-node
      image: 602401143452.dkr.ecr.us-west-1.amazonaws.com/amazon-k8s-cni:v1.8.0-eksbuild.1
      
  initContainers:
    - name: aws-vpc-cni-init
      image: 602401143452.dkr.ecr.us-west-1.amazonaws.com/amazon-k8s-cni-init:v1.8.0-eksbuild.1
```
```yaml Helm
helm upgrade -i aws-vpc-cni eks/aws-vpc-cni --namespace kube-system --set image.tag=v1.10.0-eksbuild.1 --set init.image.tag=v1.10.0-eksbuild.1
```
```yaml EKS add-on
aws eks update-addon --cluster-name <CLUSTER_NAME> --addon-name vpc-cni --addon-version v1.10.0-eksbuild.1
```
```yaml ekctl cmd
eksctl update addon --name vpc-cni --version v1.10.0-eksbuild.1 --cluster <cluster-name> --force
```
```yaml Terraform
# coming soon
```
```yaml Pulumi
# coming soon
```

For more information, see the following AWS documentation

- [Managing the Amazon VPC CNI plugin for Kubernetes add-on](https://docs.aws.amazon.com/eks/latest/userguide/managing-vpc-cni.html)

## How to fix it, short-term workaround? (Mitigation)

Use IMDSv2/tokens

## What is the impact? (Availability Impact)

The CNI driver will not start, preventing nodes from being marked as Ready and available for new Pods to be scheduled on them.

## Why does this exist? (Root Cause)

IMDSv1 uses a request/response method which can be accessed by any process that has pod `hostNetworking` attribute set to true. For hardening EKS security, it is recommended that IMDSv1 is disabled. However, in `v1.10.0`, aws-node daemonset pod requires IMDSv1 access to obtain the primary IPv4 address assigned to the Node. IMDSv1 disabled nodes will fail to be marked as ready because the conf file is not copied and the entry point script gets stuck during execution.

## Who is impacted and when? (Trigger Conditions)

_Affected Versions_

All EKS clusters or Kubernetes clusters using VPC CNI version earlier than `v1.10.0` contain this Latent Availability Risk.

_Affected Images_

One release may have multiple tags based on the image source. e.g. `v1.9.3`, `v1.9.3-eksbuild.1` are all affected tags for the version `v1.9.3`.

The official image name is \*.amazonaws.com/amazon-k8s-cni.

e.g. `602401143452.dkr.ecr.us-west-2.amazonaws.com/amazon-k8s-cni:v1.10.0-eksbuild.1` is the official image provided by AWS in `us-west-2`. 

## Additional Resources

For more information see the [associated GitHub PR](https://github.com/aws/amazon-vpc-cni-k8s/pull/1727).