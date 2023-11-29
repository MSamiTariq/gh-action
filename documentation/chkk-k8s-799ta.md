---
title: Upgrading AWS VPC CNI from version 1.10.2 to 1.11.2, causes a crash with Unbound Variable error.
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Avoid upgrading to `v1.11.2`. In case you have to upgrade, go for `v1.11.4`

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation for this Availability Risk

## What is the impact? (Availability Impact)

A crash in VPC-CNI will render the cluster unable to perform network operations and your services may face a downtime.

## Why does this exist? (Root Cause)

In AWS VPC CNI version `v1.11.2` the value of AWS_VPC_K8S_CNI_RANDOMIZESNAT is not set by default which causes VPC CNI to crash on startup. 

## Who is impacted and when? (Trigger Conditions)

_Affected Versions_

All clusters using VPC CNI versions less than `v1.11.2` are affected by this Latent Availability Risk.

## Who is impacted and when? (Trigger Conditions)

_Affected Versions_  
All clusters using Velero versions `<= 1.9.1` and `>=v1.4.0` contain this Latent Availability Risk.

## Additional Resources

For more information see the following:

- [Github Issue](https://github.com/aws/amazon-vpc-cni-k8s/issues/2027)