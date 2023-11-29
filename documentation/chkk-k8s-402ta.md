---
title: CoreDNS errors plugin not enabled
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Add and configure the `errors` plugin to CoreDNS corefile.

More information on the CoreDNS `errors` plugin can be found [here](https://coredns.io/plugins/errors/).

```yaml k8s manifest
apiVersion: v1
data:
  # errors plugin added below
  Corefile: |
    .:53 {
        errors
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

Enable `errors` plugin for CoreDNS.

## What is the impact? (Availability Impact)

Without the `errors` plugin enabled, useful error logs will not be available during CoreDNS runtime. This hinders troubleshooting and recovering from CoreDNS outages and errors.

## Why does this exist? (Root Cause)

CoreDNS `errors` plugin not enabled. No logs would be created in case of CoreDNS errors.

## Who is impacted and when? (Trigger Conditions)

_Affected Versions_  
All Kubernetes cluster using the CoreDNS as a DNS.

_Affected Images_  
All container image tags for CoreDNS.

## Additional Resources

For more details, please refer to the [official CoreDNS documentation ](https://coredns.io/plugins/errors/)