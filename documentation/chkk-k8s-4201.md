---
title: Velero panics during backup if namespace includes or excludes in Velero backup custom resource spec. evaluate to an empty list
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Upgrade or downgrade to a non-affected Velero version. See the affected versions section.

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

This defect renders Velero incapable of creating backups unless namespaces are explicitly specified.

## Why does tRhis exist? (Root Cause)

This is due to a bug in the code where Velero checks whether a backup includes or excludes any namespaces. It checks for an empty string in the first element of the namespace list, but it does not check whether the list was empty before accessing the first element. This leads to a panic when accessing the first element in the list, if the list is empty.

## Who is impacted and when? (Trigger Conditions)

_Affected Versions_  
All clusters using Velero versions `<= 1.9.1` and `>=v1.4.0` contain this Latent Availability Risk.

## Additional Resources

For more information, see:

1. [The original GitHub Issue](https://github.com/vmware-tanzu/velero/issues/5235)
2. [The PR that fixed this issue](https://github.com/vmware-tanzu/velero/pull/5236)