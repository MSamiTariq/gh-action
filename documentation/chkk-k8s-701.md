---
title: AWS EKS VPC CNI should support non-VPC pod traffic when external SNAT is disabled
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Upgrade Amazon VPC CNI to `v1.8.0` or later to apply the available patch.

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
helm upgrade -i aws-vpc-cni eks/aws-vpc-cni --namespace kube-system --set image.tag=v1.8.0-eksbuild.1 --set init.image.tag=v1.8.0-eksbuild.1
```
```yaml EKS managed Add-On
aws eks update-addon --cluster-name <CLUSTER_NAME> --addon-name vpc-cni --addon-version v1.8.0-eksbuild.1
```
```yaml ekctl
eksctl update addon --name vpc-cni --version v1.8.0-eksbuild.1 --cluster <cluster-name> --force
```
```yaml Terraform
# coming soon
```
```yaml Pulumi
# coming soon
```

For more information, see the following AWS documentation

- [Managing the Amazon VPC CNI plugin for Kubernetes Add-On](https://docs.aws.amazon.com/eks/latest/userguide/managing-vpc-cni.html)

## How to fix it, short-term workaround? (Mitigation)

1. Set `AWS_VPC_K8S_CNI_EXTERNALSNAT=true`
2. Enable external SNAT

## What is the impact? (Availability Impact)

UDP traffic from outside the VPC will not reach Pods from the secondary ENIs, disrupting the overall availability of applications.

## Why does this exist? (Root Cause)

When external SNAT is disabled, the reverse path filter for egress traffic from the VPC is not correctly set up. This leads to all ingress traffic on secondary interfaces with source IP outside of the VPC ranges to be dropped without further processing.

## Who is impacted and when? (Trigger Conditions)

_Affected Versions_

All EKS clusters or Kubernetes clusters using VPC CNI version earlier than `v1.8.0` contain this Latent Availability Risk.

_Affected Images_  
All container image tags for VPC CNI versions earlier than `v1.8.0` are affected. 

The official image name is `*.amazonaws.com/amazon-k8s-cni` e.g. `602401143452.dkr.ecr.us-west-2.amazonaws.com/amazon-k8s-cni:v1.7.5-eksbuild.1` is the official image provided by AWS in `us-west-2`. 

## Additional Resources

For more information see the [associated GitHub issue](https://github.com/aws/amazon-vpc-cni-k8s/issues/1392).