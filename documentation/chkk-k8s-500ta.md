---
title: Ensure calico-node containers fulfill package dependencies to support DNS resolution with external etcd clusters
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Upgrade calico-node to `v3.17.0` or above to apply the available patch.

For more details on upgrading Calico, please refer to the official Calico documentation here: [Upgrade Calico on Kubernetes](https://projectcalico.docs.tigera.io/maintenance/kubernetes-upgrade)

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

DNS resolution will fail, preventing hostname-IP mapping to be utilized when sending traffic between different endpoints and the external etcd cluster.

## Why does this exist? (Root Cause)

If calico-node image is missing the libresolv package, and is configured to use an external etcdv3 cluster as its datastore, this prevents using names instead of IP addresses in the etcd endpoint list.

## Who is impacted and when? (Trigger Conditions)

_Affected Versions_  
All Kubernetes clusters running calico versions  `<v3.17.0`

_Affected Images_  
Calico-node image versions  `<v3.17.0` are affected

## Additional Resources

The GitHub Pull Request with more details can be found here: [Fix DNS resolution in calico-node containers](https://github.com/projectcalico/node/pull/583)

The GitHub issue can be found [here](https://github.com/projectcalico/node/pull/583)