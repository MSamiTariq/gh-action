---
title: IP masquerade agent does not boot up on ARM nodes in GKE clusters leading to egress traffic disruption
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Upgrade your GKE control plane to one of the following or newer versions:

- `v1.21.14-gke.4300`
- `v1.22.12-gke.2300`
- `v1.23.9-gke.2100`
- `v1.24.3-gke.2100`

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

`ip-masq-agent` does not  boot up on ARM nodes in GKE clusters with control planes running the following versions,

- `v1.23.8-gke.1900`
- `v1.23.9-gke.900`
- `v1.24.2-gke.1900`
- `v1.24.3-gke.200`
- `v1.24.3-gke.900`

If `ip-masq-agent` has trouble booting up it can cause egress disruption

## Who is impacted and when? (Trigger Conditions)

_Affected Versions_  
The following GKE control plane versions contain this Latent Availability Risk:

- `v1.23.8-gke.1900`
- `v1.23.9-gke.900`
- `v1.24.2-gke.190`
- `v1.24.3-gke.200`
- `v1.24.3-gke.900`

## Additional Resources

For more information see: 

- [GKE Release notes for September 07, 2022](https://cloud.google.com/kubernetes-engine/docs/release-notes#September_07_2022)
- [Google Cloud docs on IP masquerade agent](https://cloud.google.com/kubernetes-engine/docs/concepts/ip-masquerade-agent)
- Kubernetes docs for [IP masquerading in any Kubernetes implementation](https://kubernetes.io/docs/tasks/administer-cluster/ip-masq-agent/)