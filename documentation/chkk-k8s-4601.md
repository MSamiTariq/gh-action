---
title: ListBackups operation does not work in Vitess Operator <v2.9
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Upgrade Vitess Operator to version `v2.9` or later.

## How to fix it, short-term workaround? (Mitigation)

Manually add backup parameters (flags, Volumes, VolumeMounts etc.) to the vtctld deployment spec. See the associated [Github Issue](https://github.com/planetscale/vitess-operator/issues/301) for full manifest.

```yaml
apiVersion: planetscale.com/v2
kind: VitessCluster
metadata:
  name: ope-vitess-cluster
spec:
 #... shortened for brevity
vitessDashboard:
  cells:
    - region1
  extraFlags:
    + add params here if applicable
  extraVolumeMounts:
    + add params here if applicable
  extraVolumes:
    + add params here if applicable
  replicas: 2
```

## What is the impact? (Availability Impact)

Vitess is unable to list all the backups for a shard due to this defect.

## Why does this exist? (Root Cause)

This is due to a bug in the codebase. The required flags, volumes, volume mounts and environment variables required in order for ListBackups to work were not being passed from the backup spec. to the vtctld[1] pods deployment itself. This caused Vitess to return an error with the message “no registered implementation of BackupStorage”.

## Who is impacted and when? (Trigger Conditions)

_Affected Versions_  
All clusters using Vitess Operator versions less than `v2.9.0` contain this Latent Availability Risk.

## Additional Resources

For more information, see:

1. [The original GitHub Issue](https://github.com/planetscale/vitess-operator/issues/301)
2. [The PR that fixed this issue](https://github.com/planetscale/vitess-operator/pull/356)'
3. [Vitess Documentation](https://vitess.io/docs/17.0/concepts/)

[1] vtctld is an HTTP server that lets you browse the information stored in the Topology Service. It is useful for troubleshooting or for getting a high-level overview of the servers and their current states.