---
title: AWS EKS VPC CNI in Crash Loop When No Available IP Addresses
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Upgrade to Amazon VPC CNI `v1.8.0` or above. 

```yaml k8s manifest
# Update the image for both main container and init container tag in your VPC CNI k8s manifest
  containers:
    - name: aws-node
      image: 602401143452.dkr.ecr.us-west-1.amazonaws.com/amazon-k8s-cni:v1.8.0-eksbuild.1
      
  initContainers:
    - name: aws-vpc-cni-init
      image: 602401143452.dkr.ecr.us-west-1.amazonaws.com/amazon-k8s-cni-init:v1.8.0-eksbuild.1
```
```shell Helm
helm upgrade -i aws-vpc-cni eks/aws-vpc-cni --namespace kube-system --set image.tag=v1.8.0-eksbuild.1 --set init.image.tag=v1.8.0-eksbuild.1
```
```shell EKS managed Add-On
aws eks update-addon --cluster-name <CLUSTER_NAME> --addon-name vpc-cni --addon-version v1.8.0-eksbuild.1
```
```shell eksctl cmd
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

1. Create an alarm to notify utilisation above the 80% threshold for IP addresses and adjust the pod scaling accordingly. 
2. Move to a larger EC2 instance. This will give you more IP addresses per node.
3. Use VPC CNI [Custom Networking](https://docs.aws.amazon.com/eks/latest/userguide/cni-custom-network.html) to configure a large pool of IP addresses to avoid hitting the IP address limit.

The mitigations should be considered temporary until you are able to remediate this Latent Availability Risk.

## What is the impact? (Availability Impact)

EKS VPC CNI IP address management daemon (IPAMD) will fail to operate and kubelet will not be able to create/delete pods on the node. This may lead to dangling pods on the Kubernetes worker node.

## Why does this exist? (Root Cause)

IPAMD goes into a crash loop when it runs out of IP addresses. Kubelet relies on CNI (which relies on IPAMD) to allocate/deallocate pod IP addresses. A crashing IPAMD leads to an Availability Impact for pod create/delete operations.

## Who is impacted and when? (Trigger Conditions)

_Affected Versions_  
All EKS clusters using VPC CNI version earlier than `v1.8.0` contain this Latent Availability Risk.

_Affected Images_  
All container image tags for VPC CNI versions earlier than `v1.8.0` are affected. 

The official image name is `*.amazonaws.com/amazon-k8s-cni` e.g. `602401143452.dkr.ecr.us-west-2.amazonaws.com/amazon-k8s-cni:v1.7.5-eksbuild.1` is the official image provided by AWS in `us-west-2`. 

## Additional Resources

For more information see the [associated GitHub PR](https://github.com/aws/amazon-vpc-cni-k8s/pull/1499).