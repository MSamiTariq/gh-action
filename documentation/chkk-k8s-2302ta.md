---
title: GKE Metrics Agent goes to CrashLoopBackoff in GKE v1.21 and below
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Upgrade your GKE cluster to `v1.21` or higher.

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

GKE Cloud Monitoring and Logging will not work for your cluster as long as GKE Metrics Agent is in CrashLoopBackoff.

## Why does this exist? (Root Cause)

GKE Metrics Agent goes to CrashLoopBackoff in GKE versions below `v1.21` due to an inconsistency between expected configuration and provided configuration.

## Who is impacted and when? (Trigger Conditions)

_Affected Versions_  
All GKE clusters lower than `v1.21.0` are affected by this Latent Availability Risk.

## Additional Resources

For more details, please refer to the following [Github Issue](https://issuetracker.google.com/issues/202864591)