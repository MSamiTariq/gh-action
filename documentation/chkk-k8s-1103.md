---
title: ExternalDNS v0.12.0 is unable to delete DNS records created by ExternalDNS versions <v0.12.0
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Upgrade ExternalDNS to version `v0.12.2`

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Failure to delete DNS records will cause stray records in the DNS server which can pose a security risk leading to availability issues.

## Why does this exist? (Root Cause)

Since ExternalDNS v0.12.0, new TXT format DNS records are created with a prefix which was not present in ExternalDNS versions \<0.12.0. If ExternalDNS v0.12.0 is used with a policy = ‘sync’ then it will fail to delete DNS records created by ExternalDNS versions earlier than v0.12.0. This happens because ExternalDNS version v0.12.0 expects the new format TXT records while deleting and their absence causes the delete operation to fail. 

In ExternalDNS v0.12.2, a fix has been added for the graceful migration of TXT records from older to the new format to prevent this error.

## Who is impacted and when? (Trigger Conditions)

_Affected Versions_  
All clusters using ExternalDNS version `v0.12.0` contain this Latent Availability Risk.

## Additional Resources

For more information see:

- [ExternalDNS Version 0.12.2 Release Notes](https://github.com/kubernetes-sigs/external-dns/releases/tag/v0.12.2)
- [The PR that fixed this issue](https://github.com/kubernetes-sigs/external-dns/pull/2811)