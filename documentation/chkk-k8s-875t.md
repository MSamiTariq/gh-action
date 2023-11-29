---
title: AWS Node Termination Handler is running on an incompatible version of Kubernetes
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

We strongly recommend running AWS Node Termination Handler on Kubernetes version ≥ `v1.20.`

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

AWS Node Termination Handler is not supported by the Kubernetes version you are running, which means that the software may have incompatibilities leading to unknown behavior.

## Why does this exist? (Root Cause)

Using a version of Kubernetes not compatible AWS Node Termination Handler introduces incompatibilities in your software and may lead to undefined behavior.

## Additional Resources

For more details, please refer to [Official AWS Node Termination Handler Documentation](https://docs.aws.amazon.com/prescriptive-guidance/latest/patterns/automate-deployment-of-node-termination-handler-in-amazon-eks-by-using-a-ci-cd-pipeline.html)