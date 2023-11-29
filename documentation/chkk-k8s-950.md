---
title: Traffic loss occurs on NGINX Ingress Controller restart
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Upgrade your NGINX controller to `v2.0.0` or later. See upgrade commands below:

### Pre requisites

- For NGINX Plus, please build your own image using source code.

```shell helm
# Upgrading the CRDs
# Helm does not upgrade the CRDs during a release upgrade. Before you upgrade a release, run the following command to upgrade the CRDs:
# First pull the chart sources as described here: https://docs.nginx.com/nginx-ingress-controller/installation/installation-with-helm/#pulling-the-charthttps://docs.nginx.com/nginx-ingress-controller/installation/installation-with-helm/#pulling-the-chart
$ kubectl apply -f crds/

#Note: Make sure to check the release notes for a new release for any special upgrade procedures.

# Upgrading the Release
#To upgrade the release my-release:

# Upgrade Using Chart Sources:
$ helm upgrade my-release .
 
# Upgrade via Helm Repository:
$ helm upgrade my-release nginx-stable/nginx-ingress
```

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

For clusters with a large number of resources, NGINX Ingress Controller takes minutes to start accepting client traffic and throws a connection error.

## Why does this exist? (Root Cause)

Upgrading or restarting the NGINX ingress controller processes the cluster resources (like ingresses, secrets, policies etc.) one by one. Each processing leads to the generation of a new or updated config which requires an NGINX reload. After all resources are processed, only then the NGINX ingress controller pod is considered ready to accept traffic. For clusters with a big number of resources the combined time of NGINX reloads during the start becomes significant to cause a downtime.

## Who is impacted and when? (Trigger Conditions)

Restarting or updating NGINX ingress Controller for the following versions will create and trigger this Latent Availability Risk

**Affected versions**

\< `v2.0.0`

**Affected Images**

All NGINX ingress controller container image tags for the above versions are affected.

## Additional Resources

Refer to the following links for more information.

[Install and upgrade NGINX ingress controller with manifest ](https://docs.nginx.com/nginx-ingress-controller/installation/installation-with-manifests/)  
[Upgrade  NGINX ingress controller using Helm](https://docs.nginx.com/nginx-ingress-controller/installation/installation-with-helm/#upgrading-the-chart)  
[Breaking changes for v2.0.0](https://github.com/nginxinc/kubernetes-ingress/releases/tag/v2.0.0)