---
title: Using skipRecreate flag in Sealed Secrets Controller versions prior to 0.20.2 causes CrashLoopBackOff
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Upgrade Sealed Secrets Controller to `v0.20.2` or greater.

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

This defect results in the Sealed Secrets Controller's unavailability rendering it unable to deploy and decrypt secrets. This can potentially affect the functionality and security of other cluster resources relying on those decrypted secrets.

## Why does this exist? (Root Cause)

Missing nil-safety checks on the secrets informer (in versions prior to `v0.20.2`) cause Sealed Secrets Controller to go in CrashLoopBackOff with a nil pointer dereference error.

## Who is impacted and when? (Trigger Conditions)

_Affected Versions_  
All clusters using Sealed Secrets Controller versions lesser than `0.20.2` contain this Latent Availability Risk.

## Additional Resources

For more information, please refer to the following:

- [GitHub Issue](https://github.com/bitnami-labs/sealed-secrets/issues/1151)
- [GitHub PR](https://github.com/bitnami-labs/sealed-secrets/pull/1152)