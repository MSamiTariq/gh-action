---
title: Nil Pointer Dereference causes External Secrets Operator pods to crash when generating dynamic secrets
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Upgrade your External Secrets Operator version to `v0.8.2` or greater.

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

If the External Secrets Operator Pod fails, it will no longer be able to retrieve secrets from Vault and inject them into Kubernetes. This could cause issues for any applications that rely on these secrets.

## Why does this exist? (Root Cause)

The nil pointer dereference exists due to a bug in code where a case was not being handled properly regarding missing parameters in the manifest, causing it to return a nil pointer. 

## Who is impacted and when? (Trigger Conditions)

External Secrets Operator versions `≥ 0.8.0` and versions `< v0.8.2` will have this risk.

## Additional Resources

For more information, please refer to 

1. [Github Issue](https://github.com/external-secrets/external-secrets/pull/2074#issuecomment-1548185300)
2. [PR that fixed this issue](https://github.com/external-secrets/external-secrets/pull/2321)