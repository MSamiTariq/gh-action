---
title: Regression in VPC CNI prevents IPAMD from reconciling properly leading to IP allocation failures
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Upgrade Amazon VPC CNI to `v1.12.3` or later to apply the available fix.

For more information related to upgrade, see the following AWS documentation

- [Managing the Amazon VPC CNI plugin for Kubernetes Add-On](https://docs.aws.amazon.com/eks/latest/userguide/managing-vpc-cni.html)

## How to fix it, short-term workaround? (Mitigation)

A mitigation is to downgrade VPC CNI to `v1.11.3`.

## What is the impact? (Availability Impact)

This defect prevents proper reconciliation and recovery of IP addresses, leading to IP allocation failures and potential disruptions in network connectivity when the IMDS goes out of sync and the `aws-node` restarts.

## Why does this exist? (Root Cause)

In VPC CNI `v1.11.4`, an optimization was implemented to reduce the number of EC2 calls, but it caused a regression in a specific scenario where the `PrivateIPAddressLimitExceed` error is returned. The regression occurred because the IPAMD (IP Address Management Daemon) DataStore had the ENI (Elastic Network Interface) but was missing IPs due to an out-of-sync IMDS (Instance Metadata Service). As a result, the reconciler was unable to allocate IPs correctly, leading to the error. This regression was not present in versions prior to `v1.11.4`, where IPAMD would make a call to EC2 to confirm the actual state and avoid the issue.

## Who is impacted and when? (Trigger Conditions)

**Affected versions**  

All clusters running Amazon VPC CNI versions `>=1.11.3` and `<=1.12.2` contain this Latent Availability Risk

## Additional Resources

For more details, please refer to [this GitHub PR](https://github.com/aws/amazon-vpc-cni-k8s/pull/2210).

[block:html]
{
  "html": "<br></br>"
}
[/block]


_**IPAM**: Amazon VPC IP Address Manager (IPAM) is a VPC feature that makes it easier for you to plan, track, and monitor IP addresses for your AWS workloads. You can use IPAM automated workflows to more efficiently manage IP addresses. See [this doc](https://docs.aws.amazon.com/vpc/latest/ipam/what-it-is-ipam.html) for details._

_**ENI**: An elastic network interface is a logical networking component in a VPC that represents a virtual network card. See [this doc](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-eni.html) for details._

_**IMDS**: Instance metadata is data about your instance that you can use to configure or manage the running instance. See [this doc](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-instance-metadata.html) for details._