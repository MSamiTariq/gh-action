---
title: Karpenter contains a file descriptor leak
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Upgrade your Karpenter version to `v0.29.2` or greater.

## How to fix it, short-term workaround? (Mitigation)

No mitigation or short-term workaround is available for this Availability Risk

## What is the impact? (Availability Impact)

This bug leads to a steady increase in open file descriptors because connections aren't closed properly. Over time, this results in redundant resource usage, with the system depleting its available file descriptors. This can potentially cause system performance decline or even crashes.

## Why does this exist? (Root Cause)

The underlying issue with this bug stems from Karpenter's mishandling of file descriptors, a consequence of the default behavior in Golang's HTTP client. The client failed to adequately close response bodies after obtaining a valid server response, leading to persistent open connections and active file descriptors. This flaw first appeared in Karpenter `v0.28.0`, but its impact became pronounced in `v0.29.1` due to alterations in server response dynamics.

## Who is impacted and when? (Trigger Conditions)

_Affected Versions_  
All clusters using Karpenter `v0.29.1` are affected by this Latent Availability Risk.

## Additional Resources

- [GitHub issue](https://github.com/aws/karpenter/issues/4296)
- [GitHub PR that fixes the issue](https://github.com/aws/karpenter-core/pull/416)
- [GitHub PR that has introduced this issue](https://github.com/aws/karpenter-core/pull/334/files)
- [Karpenter Upgrade Guide](https://karpenter.sh/preview/upgrade-guide/)