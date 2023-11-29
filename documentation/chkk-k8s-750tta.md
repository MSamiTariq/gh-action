---
title: Unsupported version of EKS
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

We strongly recommend upgrading your cluster to a supported version in order to stay up to date with the latest patches, features and integrations.

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

**End of Standard Support**  
At the end of EKS standard support, if your EKS version is not eligible for extended support, it will not receive security updates, technical support, and patches for EKS managed Add-Ons anymore.

**End of Extended Support**  
At the end of extended support date, new Amazon EKS clusters with the unsupported version can no longer be created. Existing control planes are automatically updated by Amazon EKS to the earliest supported version through a gradual deployment process after the end of support date. 

Following this automatic control plane update, it is imperative to perform manual updates for cluster Add-Ons and Amazon EC2 nodes, else it can result in issues that affect your cluster's overall reliability, efficiency, and availability, potentially impacting your applications and services running within the cluster.

For more information see [FAQs for Amazon EKS Extended Support](https://docs.aws.amazon.com/eks/latest/userguide/kubernetes-versions.html#extended-support-faqs).

**Note:** EKS v1.22 and below do not have extended support and have reached EOL. These versions will not receive security updates, and technical support anymore.

## Why does this exist? (Root Cause)

AWS recommends using one of their officially supported EKS versions. You can find the EKS release calendar below:

| Kubernetes version | Amazon EKS release | End of standard support | End of extended support |
| :----------------- | :----------------- | :---------------------- | :---------------------- |
| `v1.23`            | August 11, 2022    | October 11, 2023        | October 11, 2024        |
| `v1.24`            | November 15, 2022  | January 31, 2024        | January 31, 2025        |
| `v1.25`            | February 22, 2023  | May 2024                | May 2025                |
| `v1.26`            | April 11, 2023     | June 2024               | June 2025               |
| `v1.27`            | May 24, 2023       | July 2024               | July 2025               |
| `v1.28`            | September 26, 2023 | November 2024           | November 2025           |

**Amazon EKS Extended Support**

Kubernetes maintains release branches for the three most recent minor versions, each with 14 months of community support after the stable release. Amazon EKS standard support aligns with this period. With extended support, EKS clusters remain on a version for an additional 12 months after the initial 14-month support, transitioning automatically at the end of the standard support period, requiring no user intervention.

## Additional Resources

For more details, see

- [EKS documentation](https://docs.aws.amazon.com/eks/latest/userguide/kubernetes-versions.html)
- [Release Notes for EKS Extended Support](https://docs.aws.amazon.com/eks/latest/userguide/kubernetes-versions-extended.html)
- [Release Notes for EKS Standard Support](https://docs.aws.amazon.com/eks/latest/userguide/kubernetes-versions-standard.html)
- [EKS Extended Support FAQ](https://docs.aws.amazon.com/eks/latest/userguide/kubernetes-versions.html#extended-support-faqs)