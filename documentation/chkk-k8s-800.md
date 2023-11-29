---
title: Traffic drops for 30 seconds on every NGINX Ingress Controller upgrade or restart
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Upgrade to NGINX Ingress Controller `v0.49.3` or later. Please replace the tags in case you are using custom images.

```shell Helm
helm upgrade ingress-nginx ingress-nginx/ingress-nginx \
--set=controller.image.tag=v0.49.3 --set=controller.image.digest=sha256:35fe394c82164efa8f47f3ed0be981b3f23da77175bbb8268a9ae438851c8324 \
-n ingress-nginx --reuse-values
```
```yaml k8s manifest
# if your nginx deployment resource looks like (partial example)
    containers:
        - name: controller
          image: "registry.k8s.io/ingress-nginx/controller:v0.49.3@sha256:35fe394c82164efa8f47f3ed0be981b3f23da77175bbb8268a9ae438851c8324"
          ports:
```
```yaml Terraform
# coming soon
```
```yaml Pulumi
# coming soon
```

See more [here](https://kubernetes.github.io/ingress-nginx/deploy/upgrade/) on how to upgrade NGINX controller

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk Signature.

## What is the impact? (Availability Impact)

Missing Ingress hostname for 30 seconds due to faulty pod discovery in NGINX controller. This may cause a traffic outage for ~30 seconds. For external-dns users, this may result in the removal of the DNS entry for 30 seconds, on every NGINX Ingress Controller restart.

## Why does this exist? (Root Cause)

Every time the NGINX ingress controller restarts or upgrades, the controller removes the IP address field (status -> loadBalancer -> ingress -> IP) from the Ingress resource manifest. This field is used by AWS, Azure, GCP, and other cloud providers as the de-facto IP address when publishing a new service on DNS.  This missing IP address causes 100% packet loss. After ~30 seconds, the IP address is added again in the manifest, and traffic resumes.  

**Additional information**  
The IP address is removed due to a faulty logic that ignores the newly created pods due to the NGINX ingress controller upgrade/restart. It incorrectly assumes that there is no other replica of the NGINX ingress controller and removes the IP address field.

## Who is impacted and when? (Trigger Conditions)

Restarting or updating NGINX ingress Controller for the below versions will cause this Latent Availability Risk

_Affected versions_

`>=v0.42.0 and <=0.49.2 `

_Affected Images_

All NGINX ingress controller container image tags for the above versions are affected.

The community image name is `registry.k8s.io/ingress-nginx/controller:*`

Example of an affected image tag will be

`registry.k8s.io/ingress-nginx/controller:v0.47.0@sha256:a1e4efc107be0bb78f32eaec37bef17d7a0c81bec8066cdf2572508d21351d0b`

_Note: This is an example of a community shipped image. If you are running an image from a different registry we will also catch that_ 

## Additional Resources

For more information see the [associated GitHub issue](https://github.com/kubernetes/ingress-nginx/issues/7047).