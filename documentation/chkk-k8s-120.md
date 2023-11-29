---
title: Istio CoreDNS plugin has been deprecated since Istio v1.8+
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Upgrade Istio to `v1.8` and above to use native support for DNS resolution with ServiceEntries using `meshConfig.defaultConfig.proxyMetadata.ISTIO_META_DNS_CAPTURE=true`. To upgrade your version of Istio, please follow the steps given in the Official Istio Documentation [here](https://istio.io/latest/docs/setup/upgrade/)

## How to fix it, short-term workaround? (Mitigation)

Upgrade Istio to version `v1.8` or above.

## What is the impact? (Availability Impact)

Without DNS resolution set up, traffic routes between multiple sources and destinations will be disrupted across the entire cluster.

## Why does this exist? (Root Cause)

In Istio versions `v1.8` and later, `istio-coredns-plugin` has been deprecated and will not be used to provide DNS resolution as native support for DNS resolution has been added in Istio.

## Who is impacted and when? (Trigger Conditions)

_Affected Versions_  
All EKS clusters or Kubernetes clusters using Istio proxy versions `v1.8` and later.

_Affected Images_  
The container image tags for Istio proxy with version `v1.8` or above are affected.

## Additional Resources

For more details on deprecations in Istio, please refer to the [official Istio documentation](https://istio.io/latest/news/releases/1.8.x/announcing-1.8/upgrade-notes/#istio-coredns-plugin-deprecation)