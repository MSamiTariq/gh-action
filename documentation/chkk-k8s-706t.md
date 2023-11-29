---
title: AWS VPC CNI version v1.10.2 may leak IP addresses when pods are deleted
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Upgrade Amazon VPC CNI to `v1.10.3` or later to apply the available fix or downgrade to VPC CNI `v1.10.1`. 

For more information, see the following AWS documentation

- [Managing the Amazon VPC CNI plugin for Kubernetes Add-On](https://docs.aws.amazon.com/eks/latest/userguide/managing-vpc-cni.html)

## How to fix it, short-term workaround? (Mitigation)

Restart the AWS-Node Pod to make IPAMD reconcile its IP pool with the information of live Pods.

```shell
kubectl rollout restart ds aws-node -n kube-system
```

## What is the impact? (Availability Impact)

Failure to free up IP addresses used by terminated pods may result in your network running out of available IP addresses.

## Why does this exist? (Root Cause)

AWS VPC CNI `v1.10.2` introduced a change to skip CNI's delCmd when netNS is empty. This can cause IP address leaks under certain edge conditions when sandbox container was terminated(e.g. OOM), where IPAMD didn't free the IP addresses used by these terminated Pod.

## Who is impacted and when? (Trigger Conditions)

**Affected versions**  
All clusters running Amazon VPC CNI `v1.10.2` contain this Latent Availability Risk

## Additional Resources

For more details, please refer to the links below.

[GitHub Issue](https://github.com/aws/amazon-vpc-cni-k8s/issues/1939)

[PR in which the issue is fixed](https://github.com/aws/amazon-vpc-cni-k8s/pull/1941/files)