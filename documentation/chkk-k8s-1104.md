---
title: Removing a DNS record managed by external-dns v0.12.0-v0.12.2 causes all DNS records in Infoblox instances to be deleted.
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Upgrade your External DNS version to `v0.13.1` or above.

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

The impact of deleting DNS records can be widespread, affecting not only the application or service directly but also other dependent services that rely on DNS to access the affected application. This can cause a cascading effect, leading to a complete outage of the entire system resulting in lost revenue, productivity, and reputation damage.

## Why does this exist? (Root Cause)

With the migration to infoblox-go-client v2 ([in external-dns commit f890d88](https://github.com/kubernetes-sigs/external-dns/commit/f890d882e206240bdf34700a6c77775c424b5c11)), the BuildRequest has changed significantly. The search prams are no longer extracted from the object for GET API calls and therefore need to be set explicitly as query parameters. As a result every GET call returns all objects of a given record type instead of one specific object. If the result is then used to delete the object, it will delete all objects instead.

## Who is impacted and when? (Trigger Conditions)

_Affected Versions_  
All clusters using ExternalDNS versions `>= 0.12.0` and `<=v0.12.2` contain this Latent Availability Risk.

## Additional Resources

For more information see:

- [Github Issue](https://github.com/kubernetes-sigs/external-dns/issues/2931)
- [Github Issue](https://github.com/kubernetes-sigs/external-dns/issues/3070)
- [The PR that fixed this issue](https://github.com/kubernetes-sigs/external-dns/pull/2890)