---
title: Services with externalTrafficPolicy=local do not support graceful termination of pods
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Upgrade to k8s `v1.22.0` or greater and run the supported kube-proxy version.  The details of supported versions of kube-proxy in case of EKS can be find [here](https://docs.aws.amazon.com/eks/latest/userguide/managing-kube-proxy.html).

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Any pod which is in a terminating state will cause downtime if traffic is sent to it.

## Why does this exist? (Root Cause)

Services with `externalTrafficPolicy: Local` do not support graceful termination when using the iptables or ipvs mode of kube-proxy with EndpointSlices enabled. Specifically, if a connection for such a service arrives on a node when there are no "Ready" endpoints for the service, but there is at least one Terminating pod for that service on the node, then kube-proxy will send the traffic to the Terminating pod rather than dropping it. 

## Who is impacted and when? (Trigger Conditions)

_Affected Versions_  
`v1.17.x`  
`v1.18.x`  
`v1.19.x`  
`v1.20.x`  
`v1.21.x`

_Affected Images_  
All kube-proxy container images associated with the above mentioned Kubernetes versions.

## Additional Resources

For more information, please refer to

1. [Github Issue](https://github.com/kubernetes/kubernetes/issues/85643)