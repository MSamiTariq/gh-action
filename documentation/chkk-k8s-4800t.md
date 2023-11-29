---
title: Longhorn fails to backup and restore volumes behind internet proxy
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Upgrade to the latest version of longhorn or used a patch version with the fix

| Longhorn affected Version | Recommended Patch Version for Upgrading |
| ------------------------- | --------------------------------------- |
| `v1.3.0 - 1.3.2`          | `v1.3.3` or greater                     |
| `v1.11`                   | `v1.4.1` or greater                     |

For upgrade please refer to [Longhorn official documentation](https://longhorn.io/docs/latest/deploy/upgrade/longhorn-manager/)

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Inability to backup and restore volumes behind internet proxy can result in a loss of data for your system.

## Why does this exist? (Root Cause)

Longhorn fails to restore backup from behind an Internet Proxy in the affected versions because it ignores the proxy settings. This issue occurs specifically when trying to restore a backup from an S3 datastore.

## Who is impacted and when? (Trigger Conditions)

_Affected Versions_

All clusters running the following versions of Longhorn contain this Latent Availability Risk:  
`v1.3.0`,` v1.3.1`, `v1.3.2` and `v1.4.0`

## Additional Resources

For more information, please refer to [Github issue](https://github.com/longhorn/longhorn/issues/5054)