---
title: External network access does not work on AKS v1.24 running NGINX
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

There is no remediation for this Availability Risk. Please follow the steps given in the section below to mitigate this issue.

## How to fix it, short-term workaround? (Mitigation)

1. Take a Backup of the yaml of your service:

```shell
kubectl get svc ingress-nginx-controller -n ingress-basic -o yaml >> backup_service_nginx.yaml
```

2. Edit your Nginx Service to modify the annotation:

```shell
kubectl edit service -n
```

Add the following in the notations section: 

service.beta.kubernetes.io/azure-load-balancer-health-probe-request-path: /healthz

## What is the impact? (Availability Impact)

External access to AKS `v1.24` clusters using load balancer (NGINX-ingress) is blocked by default rendering it unreachable.

## Why does this exist? (Root Cause)

The health probes of the load balancer are set to use the protocols HTTP and HTTPS instead of TCP on AKS `v1.24` clusters running NGINX-ingress. This makes the cluster unreachable for all external traffic where clusters were previously configured for TCP.

1. Take a Backup of the yaml of your service:

## Who is impacted and when? (Trigger Conditions)

_Affected Versions_  
All AKS versions `>=1.24.0` and `<v1.25.0` contain this Latent Availability Risk.

## Additional Resources

For more information, please refer to this [GitHub issue](https://github.com/Azure/AKS/issues/3210)