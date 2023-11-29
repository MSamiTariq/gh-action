---
title: CoreDNS health plugin not enabled
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Add and configure the `health` plugin to CoreDNS corefile.

More information on the CoreDNS `health` plugin can be found [here](https://coredns.io/plugins/health/):

```yaml k8s manifest
apiVersion: v1
data:
  # health plugin added below
  Corefile: |
    .:53 {
        health
        kubernetes cluster.local in-addr.arpa ip6.arpa {
          pods insecure
          fallthrough in-addr.arpa ip6.arpa
        }
    }
kind: ConfigMap
metadata:
  labels:
    eks.amazonaws.com/component: coredns
    k8s-app: kube-dns
  name: coredns
  namespace: kube-system
```
```yaml Terraform
# coming soon
```
```yaml Pulumi
# coming soon
```

## How to fix it, short-term workaround? (Mitigation)

Enable `health` plugin for CoreDNS.

## What is the impact? (Availability Impact)

Without the `health` plugin enabled, you will be unaware of the latest health and availability. This reduces the chances of detecting and recovering from CoreDNS outages and errors.

## Why does this exist? (Root Cause)

CoreDNS `health` plugin not enabled. CoreDNS will not have a health check endpoint created and configured.

## Who is impacted and when? (Trigger Conditions)

_Affected Versions_  
All Kubernetes cluster using the CoreDNS as a DNS.

_Affected Images_  
All container image tags for CoreDNS.

## Additional Resources

For more details, please refer to the [official CoreDNS documentation ](https://coredns.io/plugins/health/)