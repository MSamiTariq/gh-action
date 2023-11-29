---
title: Ingress GCE Controller stuck in CrashLoop on GKE clusters running Kubernetes verison v1.24 or later.
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

There is no remediation for this Availability Risk. Please follow the steps given in the section below to mitigate this issue.

## How to fix it, short-term workaround? (Mitigation)

Delete any Services with .spec.ports undefined.

## What is the impact? (Availability Impact)

This issue will result in the lack of ability to provide L7 Ingress, L4 Internal LoadBalancer Service with Subsetting turned on, and L4 Network LoadBalancer based on Regional Backend Services in the cluster.

## Why does this exist? (Root Cause)

Newly created GKE Clusters on Kubernetes `v1.24` or later using Services without .spec.ports field defined will cause a crash-loop of the ingress-gce controller (l7lbcontroller pod). This will result in the inability to use Ingress or LoadBalancer services.

## Who is impacted and when? (Trigger Conditions)

_Affected Versions_  
All GKE versions `>= 1.24.0` contain this Latent Availability Risk.

## Additional Resources

For more information please refer to the [GKE Release Notes.](https://cloud.google.com/kubernetes-engine/docs/release-notes#August_19_2022)