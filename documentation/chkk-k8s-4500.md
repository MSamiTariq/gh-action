---
title: The detected Kubelet version is not compatible with your Kubernetes Control Plane version
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Use a version of Kubelet that is the same as the version of your Kubernetes Control Plane.

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Running an unsupported version combination of Kubelet and Kubernetes Control Plane will lead to unintended behavior and functionality may not work as expected.

## Why does this exist? (Root Cause)

The [Kubernetes project](https://kubernetes.io/releases/version-skew-policy/#kubelet) allows a version skew of N-3 between the Control Plane and Kubelet. Similarly, [GKE](https://cloud.google.com/kubernetes-engine/docs/concepts/cluster-upgrades) allows Nodes to run a Kubernetes version that is no more than 3 minor versions less than the Control Plane version. However, by default, GKE clusters are created with the same Kubernetes versions for the Control Plane and Nodes. [EKS](https://docs.aws.amazon.com/eks/latest/userguide/kubernetes-versions.html) recommends using the same versions for Control Plane and Kubelet. 

Therefore, we recommend using the same minor versions of Kubernetes for your Control Plane and Nodes.

## Additional Resources

For more information, see the following links:

[EKS Userguide FAQ Section](https://docs.aws.amazon.com/eks/latest/userguide/kubernetes-versions.html)

[Kubelet section in Kubernetes Version Skew Policy page](https://kubernetes.io/releases/version-skew-policy/#kubelet)

[GKE Cluster Upgrades Guide](https://cloud.google.com/kubernetes-engine/docs/concepts/cluster-upgrades)