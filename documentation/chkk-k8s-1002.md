---
title: Memory leak in Traefik leads to pod and/or node failure
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Upgrade to Traefik Ingress Controller to `v2.5.7` or later.

```yaml k8s manifest
# if your traefik deployment resource looks like (partial example)
    containers:
        - name: traefik
          image: "traefik:2.5.70@sha256:64e13dc2f241f9d021eda736f5a7c3dc81c113554dd611a9c52340a5e3b7843b"
          ports:
```
```yaml Helm
helm upgrade traefik traefik/traefik --set=image.tag=v2.5.7 --set=image.digest=sha256:64e13dc2f241f9d021eda736f5a7c3dc81c113554dd611a9c52340a5e3b7843b  --reuse-values
```
```yaml Terraform
# coming soon
```
```yaml Pulumi
# coming soon
```

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Traefik pods (in Deployment or Daemonset both) will run out of memory and lead to traffic outage for the time Traefik is down. If unbounded, the nodes running Traefik proxy will also run out of memory, increasing the blast radius to the node and taking down other applications running on the affected node. 

## Why does this exist? (Root Cause)

Traefik introduced a memory leak in `v2.2.x` where container_memory_rss and container_memory_working_set_bytes continue to increase until the pod or the node runs out of memory.

## Who is impacted and when? (Trigger Conditions)

_Affected Versions_  
All Traefik ingress controller versions between `v2.2.0` and `v2.5.7` contain this Latent Availability Risk (LAR)

## Additional Resources

Details of the exact Github issue can be found [here](https://github.com/traefik/traefik/issues/7964)