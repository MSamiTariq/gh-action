---
title: XDS v2 API has been deprecated for EnvoyFilter in Istio v1.9+
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

```yaml
apiVersion: networking.istio.io/v1alpha3
kind: EnvoyFilter
metadata:
  name: add-header
spec:
  configPatches:
  - applyTo: HTTP_FILTER
    match:
      context: SIDECAR_OUTBOUND
      listener:
        filterChain:
          filter:
+            name: envoy.filters.network.http_connection_manager
            subFilter:
+              name: envoy.filters.http.router
    patch:
      operation: INSERT_BEFORE
      value:
        name: envoy.lua
        typed_config:
+          "@type": type.googleapis.com/envoy.extensions.filters.http.lua.v3.Lua
          inlineCode: |
            function envoy_on_request(handle)
              handle:headers():add("foo", "bar")
            end
```
```yaml Terraform
# coming soon
```
```yaml Pulumi
# coming soon
```

In general, it is also recommended that EnvoyFilters are applied to a specific version in order to ensure that Envoy changes do not break them during upgrade. This can be done with a match clause as shown below:

```yaml
match:
  proxy:
    proxyVersion: ^1\.9.*
```

For more details on configuring EnvoyFilter with Istio, please refer to the official Istio documentation here:  
[Istio-Release-Notes](https://istio.io/latest/news/releases/1.9.x/announcing-1.9/upgrade-notes/#envoyfilter-xds-v2-removal)

## How to fix it, short-term workaround? (Mitigation)

EnvoyFilters should be applied to a specific version to ensure Envoy changes do not break them during upgrade.

## What is the impact? (Availability Impact)

The Envoy proxy will reject the configuration and be unable to receive updated configurations, preventing cluster updates and causing the cluster to go out of sync with the latest changes. 

## Why does this exist? (Root Cause)

Envoy has removed support for the XDS v2 API in Istio versions `v1.9` and later. EnvoyFilters depending on these APIs must be updated before upgrading.

## Who is impacted and when? (Trigger Conditions)

_Affected Versions_  
All EKS clusters or Kubernetes clusters using Istio proxy versions including and later than `v1.9`

_Affected Images_  
The container image tags for Istio proxy with version `v1.9` and above running on Kubernetes `v1.22` or above are affected.

## Additional Resources

Exact details can be found [here](https://istio.io/latest/news/releases/1.9.x/announcing-1.9/upgrade-notes/#envoyfilter-xds-v2-removal)