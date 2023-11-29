---
title: DNS resolver in AKS stops working on Ubuntu 18.04
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Upgrade Node image version to `AKSUbuntu-1804gen2containerd-2022.08.10` or later.

```shell
az aks upgrade \
    --resource-group <RESOURCE_GROUP> \
    --name <CLUSTER_NAME> \
    --node-image-only
```

## How to fix it, short-term workaround? (Mitigation)

Restart the affected nodes' VM instances.

## What is the impact? (Availability Impact)

AKS clusters with nodes running Ubuntu 18.04 image are unable to resolve DNS queries resulting in nodes not able to connect outside the cluster. If coredns is mounted on the affected node, the pod would go into crashloop. The node will also be unable to pull images from external sources.

## Why does this exist? (Root Cause)

A systemd upgrade on the Ubuntu 18.04 caused a regression in the systemd-resolved service, resulting in missing DHCP leases and DNS resolution failures. 

## Who is impacted and when? (Trigger Conditions)

_Cloud Provider_  
Microsoft AKS

_Affected Images_  
`AKSUbuntu-1804gen2containerd-2022.07.04` 

## Additional Resources

The details of the issue can be found [here](https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1988119).

Helpful resources:  
[systemd](https://wiki.ubuntu.com/systemd)  
[DHCP Leases](https://manpages.ubuntu.com/manpages/xenial/man5/dhcpd.leases.5.html)