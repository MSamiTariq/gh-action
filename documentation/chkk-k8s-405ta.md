---
title: CoreDNS panics when reload and kubernetes plugins are enabled
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Upgrade CoreDNS `v1.8.6` or above

Given below are the commands for upgrade. The image name will change depending upon where it is hosted.  
So replace the image name before proceeding

In case of ecr it is  `*.dkr.ecr.*.amazonaws.com/eks/coredns:v*-eksbuild.*`

for e.g `602401143452.dkr.ecr.us-west-2.amazonaws.com/eks/coredns:v1.8.6-eksbuild.1`

In case of gcr it is `k8s.gcr.io/coredns/coredns:*`

for e.g  `k8s.gcr.io/coredns/coredns:v1.8.6`

```yaml k8s manifest
spec:
      containers:
      - args:
        - -conf
        - /etc/coredns/Corefile
        image: 602401143452.dkr.ecr.us-west-2.amazonaws.com/eks/coredns:v1.8.6-eksbuild.1
```
```yaml Helm
helm upgrade coredns coredns/coredns -n kube-system --set=image.tag=1.8.6
```
```yaml Terraform
# coming soon
```
```yaml Pulumi
# coming soon
```

## How to fix it, short-term workaround? (Mitigation)

- Upgrade CoreDNS to `v1.8.6` or above.
- Remove the `reload` plugin from the CoreDNS corefile.

## What is the impact? (Availability Impact)

In CoreDNS `v1.8.5`, with both `reload` and `kubernetes` plugins enabled, the instance will panic and stop running. This will cause name resolution failures and potential downtime.

## Why does this exist? (Root Cause)

With both `reload` and `kubernetes` plugins enabled in CoreDNS `v1.8.5`, the instance will panic and exit.

## Who is impacted and when? (Trigger Conditions)

_Affected Versions_  
All Kubernetes cluster using CoreDNS `v1.8.5` as a DNS.

_Affected Images_  
Container image for CoreDNS `v1.8.5` is affected.

## Additional Resources

Details of the exact github issue can be found [here](https://github.com/coredns/coredns/issues/4880).