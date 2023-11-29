---
title: Pulsar is not compatible with your Kubernetes version
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation))

Upgrade your Kubernetes cluster to `v1.18` or greater.

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Running an unsupported version combination of Pulsar and Kubernetes can lead to unintended behavior and functionality may not work as expected.

## Why does this exist? (Root Cause)

As per the documentation, a Kubernetes cluster `v1.18` is considered as a pre-requisite to deploy Pulsar.

## Additional Resources

For more information, please refer to the [Official Pulsar Documentation](https://pulsar.apache.org/docs/next/helm-prepare/#create-kubernetes-cluster).