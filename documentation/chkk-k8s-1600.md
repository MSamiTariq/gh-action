---
title: Jenkins Operator is incompatible with your current version of Kubernetes
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

We strongly recommend upgrading your cluster’s Kubernetes version to a supported version (`> v1.17`) as per the requirements of the Jenkins Operator.

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Jenkins Operator does not support the Kubernetes version you are running, which means that the software may have incompatibilities leading to unknown behavior. 

## Why does this exist? (Root Cause)

As per the requirements by Jenkins Operator, the current release requires a Kubernetes cluster version greater than `v1.17`.

## Additional Resources

For more information refer to [Jenkins Operator Documentation](https://jenkinsci.github.io/kubernetes-operator/docs/getting-started/latest/installing-the-operator/#requirements)