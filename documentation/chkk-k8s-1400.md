---
title: You are using a supported but an unrecommended version of containerd with Kubernetes version 1.24
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Use one the following recommended containerd versions: `v1.5.11` and later or `v1.6.4` and later.

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Using an unrecommended version of containerd with Kubernetes `v1.24` may lead to CNI plugin-related errors. This will cause containers to not run properly and lead to an unknown behavior.

## Why does this exist? (Root Cause)

containerd  `v1.6.0`-`v1.6.3` require CNI plugins and/or CNI config versions to be manually upgraded or declared and thus may lead to errors that have been resolved in the recommended containerd versions. 

## Additional Resources

For more details, please refer to the following links:  
[CNI plugin-related errors](https://github.com/kubernetes/website/blob/dev-1.24/content/en/docs/tasks/administer-cluster/migrating-from-dockershim/troubleshooting-cni-plugin-related-errors.md)  
[official Kubernetes documentation](https://github.com/containerd/containerd#hello-kubernetes-v124)