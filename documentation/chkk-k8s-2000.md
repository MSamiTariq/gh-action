---
title: Incompatible version of Kubernetes with ArgoCD
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Use an ArgoCD release that is compatible with your Kubernetes version. See the following table,

| ArgoCD Version |   Kubernetes Version   |
| :------------: | :--------------------: |
|       2.9      | 1.28, 1.27, 1.26, 1.25 |
|       2.8      | 1.27, 1.26, 1.25, 1.24 |
|       2.7      | 1.26, 1.25, 1.24, 1.23 |

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Using ArgoCD with an incompatible version of Kubernetes is not recommended. Using an incompatible version combination may cause your software to run into issues and functionality may not work as expected.

## Why does this exist? (Root Cause)

Each version of ArgoCD has been tested with a range of specific Kubernetes versions that are considered as compatible and defined within the table above.

## Additional Resources

For more information, see:

- [ArgoCD and Kubernetes Tested Versions](https://argo-cd.readthedocs.io/en/stable/operator-manual/installation/#tested-versions)
- [ArgoCD Release Cadence](https://argo-cd.readthedocs.io/en/stable/developer-guide/release-process-and-cadence/)