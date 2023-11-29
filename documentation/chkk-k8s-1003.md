---
title: Traefik RateLimit middleware CRD does not enforce sourceCriterion
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Upgrade to Traefik Ingress Controller to `v2.5.5` or above.

```yaml k8s manifest
# edit your traefik deployment resource to look like this (partial example)
    containers:
        - name: traefik
          image: traefik:2.5.5
          ports:
```
```yaml Helm
helm upgrade --reuse-values traefik traefik/traefik
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

Traefik RateLimit middleware will not enforce the user provided sourceCriterion and will instead use the default value of ​​request's remote address field (as an ipStrategy)

## Why does this exist? (Root Cause)

Traefik RateLimit middleware Kubernetes CRD does not enforce sourceCriterion. Source IP and ranges will have no impact on the rate limit requests. 

## Who is impacted and when? (Trigger Conditions)

_Affected Versions_  
If you’re using sourceCriterion in the RateLimit middleware and running Traefik Ingress controller version lower than `v2.5.5` then this Latent Availability Risk (LAR) exists.

```yaml Middleware
apiVersion: traefik.containo.us/v1alpha1
kind: Middleware
metadata:
  name: test-ratelimit
spec:
  rateLimit:
    sourceCriterion:
      ipStrategy:
        depth: 2
```

_Affected Images_  
Container images for Traefik are affected.

## Additional Resources

For more information see the associated [GitHub issue](https://github.com/traefik/traefik/issues/8590).