---
title: CoreDNS loop plugin not enabled
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Add and configure the `loop` plugin to CoreDNS corefile.

More information on the CoreDNS `loop` plugin can be found [here](https://coredns.io/plugins/loop/):

```yaml k8s manifest
apiVersion: v1
data:
  # loop plugin added below
  Corefile: |
    .:53 {
        loop
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

Enable `loop` plugin for CoreDNS.

## What is the impact? (Availability Impact)

Without the `loop` plugin enabled, no forwarding loops will be detected in CoreDNS. This can use up excessive amounts of node resources and likely cause latency issues.

## Why does this exist? (Root Cause)

CoreDNS `loop` plugin not enabled. CoreDNS would not stop the server when a forwarding loop is encountered.

## Who is impacted and when? (Trigger Conditions)

_Affected Versions_  
All Kubernetes cluster using the CoreDNS as a DNS.

_Affected Images_  
All container image tags for CoreDNS.

## Additional Resources

For more details, please refer to the [official CoreDNS documentation](https://coredns.io/plugins/loop/)