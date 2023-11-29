---
title: The detected RabbitMQ Cluster Operator version is not compatible with your Kubernetes version
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Use a version of RabbitMQ Cluster Operator that is supported for your Kubernetes version. RabbitMQ supports Kubernetes versions `v1.19+` for its Cluster Operator. 

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Running an unsupported version combination of RabbitMQ Cluster Operator and Kubernetes can lead to unintended behavior and functionality may not work as expected.

## Why does this exist? (Root Cause)

RabbitMQ recommends using a supported version of Kubernetes control plane.

## Additional Resources

For more information see: [RabbitMQ Cluster Operator compatibility](https://rabbitmq.com/kubernetes/operator/install-operator.html#compatibility)