---
title: CoreDNS reload plugin not enabled
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Add and configure the `reload` plugin to CoreDNS corefile.

```yaml k8s manifest
apiVersion: v1
data:
  # loop plugin added below
  Corefile: |
    .:53 {
        reload
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

Enable `reload` plugin for CoreDNS.

## What is the impact? (Availability Impact)

Without the `reload` plugin enabled, changes made to CoreDNS corefile will not be automatically applied. This can result in unexpected behavior due to the older config still being used.

## Why does this exist? (Root Cause)

CoreDNS `reload` plugin not enabled. Changes made to the CoreDNS corefile will not be automatically applied.

## Who is impacted and when? (Trigger Conditions)

_Affected Versions_  
All Kubernetes clusters using the CoreDNS as a DNS.

_Affected Images_  
All container image tags for CoreDNS.

## Additional Resources

For more details, please refer to the official [CoreDNS documentation](https://coredns.io/plugins/reload/).