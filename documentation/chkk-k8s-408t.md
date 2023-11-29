---
title: CoreDNS OOM Killed on DNS queries spikes and scale
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

1. Add [horizontal auto-scaling](https://kubernetes.io/docs/tasks/administer-cluster/dns-horizontal-autoscaling/#enablng-dns-horizontal-autoscaling) for the CoreDNS Deployment based on the number of nodes and CPU cores in the cluster (preferred)

2. Use [NodeLocal DNSCache](https://kubernetes.io/docs/tasks/administer-cluster/nodelocaldns/). This will improve the DNS performance as every node will run a DNS caching agent as a DaemonSet. All DNS queries will be handled by the DNS caching agent running on the node instead of using central kube-dns Service

## How to fix it, short-term workaround? (Mitigation)

1. Increase memory requests/limits to greater than 200Mi (based on your scale)
2. Increase number of CoreDNS replicas to 5 or more (based on your scale)

The mitigations should be considered temporary until you are able to remediate this Latent Availability Risk.

## What is the impact? (Availability Impact)

Cluster wide total outage and denial of service (DoS) when DNS queries are spiked and CoreDNS reaches it’s memory limits. CoreDNS outage has cluster wide blast radius.

## Why does this exist? (Root Cause)

A sudden spike in DNS queries can lead to CoreDNS running out of memory and getting OOM Killed.

## Who is impacted and when? (Trigger Conditions)

_Affected Versions_  
All CoreDNS versions

_Affected Images_  
All CoreDNS image versions

## Additional Resources

Details of the exact Github issue can be found [here](https://github.com/kubernetes/kops/issues/5652)