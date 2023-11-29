---
title: Unsupported version of ArgoCD
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

We strongly recommend upgrading ArgoCD to one of the three supported minor versions which are: `v2.9`  `v2.8` and `v2.7`. For more information regarding upgrading ArgoCD version see: [ArgoCD upgrade guide](https://argo-cd.readthedocs.io/en/stable/operator-manual/upgrading/overview/)

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Running an ArgoCD version that has reached end of support can lead to unintended behavior and functionality may not work as expected.

## Why does this exist? (Root Cause)

Argo CD patch releases occur on an as-needed basis. Only the three most recent minor versions are eligible for patch releases. Versions older than the three most recent minor versions are considered EOL and will not receive bug fixes or security updates.

Please note that bug fixes and/or security updates can be back-ported in earlier releases which may have reached EOL. This is done through community support and the support policy given at the link below is the official one that the maintainers follow.

## Additional Resources

For more information see 

- [ArgoCD's Release Cadence and Support](https://argo-cd.readthedocs.io/en/stable/developer-guide/release-process-and-cadence/#patch-releases-eg-25x:~:text=Versions%20older%20than%20the%20three%20most%20recent%20minor%20versions%20are%20considered%20EOL%20and%20will%20not%20receive%20bug%20fixes%20or%20security%20updates.).
- [ArgoCD's Security Policy](https://github.com/argoproj/argo-cd/security/policy#supported-versions:~:text=We%20currently%20support%20the%20last%203%20minor%20versions%20of%20Argo%20CD%20with%20security%20and%20bug%20fixes.)
- [ArgoCD upgrade guide](https://argo-cd.readthedocs.io/en/stable/operator-manual/upgrading/overview/)