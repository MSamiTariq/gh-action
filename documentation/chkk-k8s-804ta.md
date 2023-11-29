---
title: Ingress NGINX Controller gets stuck in CrashLoopBackOff due to retry failures
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Upgrade Ingress NGINX Controller to version `v1.2.0` or newer. Refer to the [upgrade guide](https://kubernetes.github.io/ingress-nginx/deploy/upgrade/) for detailed steps.

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

This defect can lead to ingress traffic disruption, performance degradation and increased load on your cluster.

## Why does this exist? (Root Cause)

This defect exists due to a bug in the exponential backoff retry logic. The implementation does not retry according to the retry policy. The backoff factor for the retry is also set to 0.8. This less than 1 value, causes the delay between each retry to get shorter and shorter. As a consequence this implementation does not achieve the same effect of adaptively polling for a process that may take a long time. This can cause the controller pod to get stuck in CrashLoopBackoff during startup.

This was fixed by reimplementing the retry logic so that retries are performed as intended by the retry policy. The backoff factor was also set to 1.3 (> 1).

## Who is impacted and when? (Trigger Conditions)

_Affected Images and Versions_

- `>=v0.34.0` and `<v1.2.0` for the image `ingress-nginx/controller` 
- `>=v0.21.0` and `<v0.34.0` for the image `kubernetes-ingress-controller/nginx-ingress-controller`

## Additional Resources

For more information, see [this GitHub PR](https://github.com/kubernetes/ingress-nginx/pull/8325).