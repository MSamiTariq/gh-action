---
title: Deleting a cluster with xDS cache disabled could crash Istio
category: 655c49ff76fdad0024723139
---

_**Note: This Latent Availability Risk is only applicable to a multicluster mesh (i.e. Istio mesh installed across multiple clusters).**_

## How to fix it, long-term fix? (Remediation)

Upgrade your Istio version to `v1.18.1` or greater

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Istiod is responsible for managing the control plane of the Istio service mesh. If it crashes, it can cause the service mesh to stop working properly. This can cause issues such as service disruptions and downtime for any applications that depend on the service mesh.

## Why does this exist? (Root Cause)

The defect occurred because the code didn't handle a particular case correctly, which resulted in returning a nil pointer. Accessing this nil pointer triggered a nil pointer dereference error, causing Istio to crash.

## Who is impacted and when? (Trigger Conditions)

Istio versions `≥ 1.14.0` and versions `< v1.18.1` will have this risk.

## Additional Resources

For more information, please refer to 

1. [Github Issue](https://github.com/istio/istio/issues/45798)

2. [PR that fixed this issue](https://github.com/istio/istio/pull/45800)