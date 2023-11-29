---
title: Unsupported version of kube-state-metrics
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

We recommend upgrading kube-state-metrics to the latest release which is `v2.10.0`. You can find more information about kube-state-metrics' releases on their official [GitHub release page](https://github.com/kubernetes/kube-state-metrics/releases/).

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Running a kube-state-metrics version that has reached end of support can lead to unintended behavior and functionality may not work as expected.

## Why does this exist? (Root Cause)

kube-state-metrics only supports the latest release at any given time. As per their documentation:  
_Be aware, that the maintainers will only support the latest release. Older versions might be supported by interested users of the community_.

## Additional Resources

For more information see kube-state-metric's official [GitHub documentation](https://github.com/kubernetes/kube-state-metrics#compatibility-matrix:~:text=Be%20aware%2C%20that%20the%20maintainers%20will%20only%20support%20the%20latest%20release.%20Older%20versions%20might%20be%20supported%20by%20interested%20users%20of%20the%20community.).