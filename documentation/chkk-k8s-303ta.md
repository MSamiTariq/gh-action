---
title: cert-manager versions prior to v1.11.2 are liable to crash on Kubernetes v1.27.x
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Upgrade your cert-manager version to `v1.11.2` or greater.

You can upgrade cert-manager using the following sample commands. Please note that before running them in your environment, you should contextualise the commands with values specific to your environment. 

```shell shell
helm repo add jetstack <https://charts.jetstack.io>
helm repo update jetstack
helm upgrade --set installCRDs=true --version <version> <release_name> jetstack/cert-manager
```

Or refer to the official [cert-manager upgrade guide](https://cert-manager.io/docs/installation/upgrading/) for more information

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

cert-manager crashing can lead to the disruption of certificate management operations, potentially causing services relying on valid certificates to become unavailable. This can result in security vulnerabilities and hinder communication between services, impacting the overall availability of the cluster.

## Why does this exist? (Root Cause)

When running cert-manager versions prior to `v1.11.2` with Kubernetes `v1.27`, an issue arises due to an incompatible version of client libraries. As a consequence, cert-manager encounters a segmentation fault, which indicates an attempt to access an unauthorized memory location.

## Who is impacted and when? (Trigger Conditions)

_Affected Versions_  
All clusters using cert-manager versions lesser than `v1.11.2` contain this Latent Availability Risk.

## Additional Resources

For more details, please refer to the following:

- [GitHub Issue](https://github.com/cert-manager/cert-manager/issues/6033)