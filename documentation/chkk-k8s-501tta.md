---
title: Calico should maintain local routes for routing traffic to multiple Pods at scale
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Upgrade calico to `v3.21.3` or above to apply the available patch.

For more details on upgrading Calico, please refer to the official Calico documentation here: [Upgrade Calico on Kubernetes](https://projectcalico.docs.tigera.io/maintenance/kubernetes-upgrade)

## How to fix it, short-term workaround? (Mitigation)

Rollout restart the calico typha deployment.

## What is the impact? (Availability Impact)

Calico will use stale information in clusters with >500 policies/pods/etc causing it to remove local host routes to some Pods. This will disrupt traffic and impact availability of applications.

## Why does this exist? (Root Cause)

Due to a bug in the Kubernetes client while making paged list calls, in a cluster with >500 resources (e.g. policies/pods), the datastore watcher may get stuck and report stale information about running Pods to calico. This will cause significant memory increase in calico typha as well as impact applications running in the affected pods.

## Who is impacted and when? (Trigger Conditions)

_Affected Versions_  
All Kubernetes clusters running calico versions  `>= v3.21.0` and `<v3.21.3`

_Affected Images_  
Calico-node image versions `>=v3.21.0` and `<v3.21.3` are affected

## Additional resources

The exact GitHub issues can be found here: [Route entries get deleted by felix due to stale data from typha](https://github.com/projectcalico/calico/issues/5173)

Also see the [release notes](https://projectcalico.docs.tigera.io/archive/v3.21/release-notes/)  for Calico `v3.21`