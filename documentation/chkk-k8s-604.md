---
title: There should be no leading or trailing whitespaces in loadBalancerSourceRanges
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Upgrade to the latest patch version of kube-proxy. Please see the list below of minor versions and their subsequent patch versions which contain the fix:

| Minor Version | Patch Version                    |
| :------------ | :------------------------------- |
| `v1.19.x`     | Upgrade to `v1.19.4` or greater  |
| `v1.18.x`     | Upgrade to `v1.18.11` or greater |
| `v1.17.x`     | Upgrade to `v1.17.14` or greater |

Given below are the commands for upgrade.  The image name will change depending upon where it is hosted.  
So replace the image name before proceeding

In case of  ecr  it is \*.dkr.ecr.\*.amazonaws.com/eks/kube-proxy:v\*-eksbuild.\*

for e.g  `602401143452.dkr.ecr.us-west-2.amazonaws.com/eks/kube-proxy:v1.19.4-eksbuild.1`

In case of gcr it is  k8s.gcr.io/kube-proxy:\*

for e.g: `k8s.gcr.io/kube-proxy:v1.19.4`

```yaml k8s manifest
# if your daemonset resource looks like (partial example)

    containers:
        - name: kube-proxy
          image:602401143452.dkr.ecr.us-west-2.amazonaws.com/eks/kube-proxy:v1.19.4-eksbuild.1
```
```yaml Terraform
# coming soon
```
```yaml Pulumi
# coming soon
```

More information regarding kube-proxy upgrade on eks environment can be find [here](https://docs.aws.amazon.com/eks/latest/userguide/managing-kube-proxy.html#updating-kube-proxy-eks-add-on).

## How to fix it, short-term workaround? (Mitigation)

Remove leading or trailing whitespaces in loadBalancerSourceRanges.

## What is the impact? (Availability Impact)

Any leading or trailing whitespaces in loadBalancerSourceRanges will cause the service to fail.

## Why does this exist? (Root Cause)

Kube-Proxy does not automatically trim whitespaces to match validation in loadBalancerSourceRanges field.

## Who is impacted and when? (Trigger Conditions)

_Affected Versions_  
`v1.19.0 - v1.19.3`  
` v1.18.0 - v1.18.10`  
` v1.17.0 - v1.17.13`

_Affected Images_  
All kube-proxy images in the above mentioned kubernetes versions.

## Additional Resources

The GitHub pull request with more details can be found [here](https://github.com/kubernetes/kubernetes/pull/94107)