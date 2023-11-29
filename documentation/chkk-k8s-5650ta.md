---
title: The detected Netdata version is not compatible with your Kubernetes version
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Use a version of Netdata that is supported for your Kubernetes version. Netadata supports Kubernetes versions `v1.9+` only. 

For more information see the [official docs](https://github.com/netdata/netdata/blob/master/packaging/installer/methods/kubernetes.md#:~:text=A%20working%20cluster%20running%20Kubernetes%20v1.9%20or%20newer).

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Running an unsupported version combination of Netdata and Kubernetes can lead to unintended behavior and functionality may not work as expected.

## Why does this exist? (Root Cause)

Netdata recommends using a supported version of Kubernetes control plane.

## Additional Resources

For more information see: [Netdata compatibility](https://github.com/netdata/netdata/blob/master/packaging/installer/methods/kubernetes.md#:~:text=A%20working%20cluster%20running%20Kubernetes%20v1.9%20or%20newer)