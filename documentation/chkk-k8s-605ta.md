---
title: UDP Pod behind a LoadBalancer Service (External IP) requires manual conntrack flushing
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Upgrade to the following recommended version of kube-proxy in case you're using `v1.20` or `v1.21`. Please see the list below of minor versions and their subsequent patch versions which contain the fix:

| Minor Version | Patch Version                    |
| :------------ | :------------------------------- |
| `1.20.x`      | Upgrade to `v1.20.11` or greater |
| `1.21.x`      | Upgrade to `v1.21.5` or greater  |

Given below are the commands for upgrade. The image name will change depending upon where it is hosted.  
So replace the image name before proceeding

In case of ecr it is `*.dkr.ecr.*.amazonaws.com/eks/kube-proxy:v*-eksbuild.*`

for e.g `602401143452.dkr.ecr.us-west-2.amazonaws.com/eks/kube-proxy:v1.21.5-eksbuild.1`

In case of gcr it is `k8s.gcr.io/kube-proxy:*`

for e.g: `k8s.gcr.io/kube-proxy:v1.21.5`

```yaml k8s manifest
# if your daemonset resource looks like (partial example)

    containers:
        - name: kube-proxy
          image:602401143452.dkr.ecr.us-west-2.amazonaws.com/eks/kube-proxy:v1.21.5-eksbuild.1
```
```yaml Terraform
# coming soon
```
```yaml Pulumi
# coming soon
```

## How to fix it, short-term workaround? (Mitigation)

Manually delete all stale conntrack entries to allow udp packet flow into the new pod

## What is the impact? (Availability Impact)

UDP traffic to a Pod behind a LoadBalancer exposing a UDP listener service is blackholed when the replacement Pod is scheduled on the same node as the old Pod.

## Why does this exist? (Root Cause)

When a pod, exposed by a UDP Service, gets deleted, its conntrack entries need to be manually flushed after the iptable rules are programmed otherwise stale conntrack entries will cause the traffic to flow to the deleted pod.

## Who is impacted and when? (Trigger Conditions)

_Affected Versions_  
`v1.18.x`  
`v1.19.x`  
`v1.20.0` - `v1.20.10`  
`v1.21.0` - `v1.21.4`  
`v1.22.0`

_Affected Images_  
All kube-proxy container images associated with the above mentioned Kubernetes versions.

## Additional Resources

The GitHub issue with more details can be found [here](https://github.com/kubernetes/kubernetes/issues/103857)