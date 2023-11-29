---
title: Host systems are required to run Linux kernel version 4.9.17 or later to run a Cilium agent
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Upgrade the host Linux version to `v4.9.17` or later

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Linux kernel version does not meet official Cilium install system requirements.

## Why does this exist? (Root Cause)

Cilium leverages and builds on the kernel eBPF functionality as well as various subsystems which integrate with eBPF. Therefore, host systems are required to run Linux kernel version `v4.9.17` or later to run a Cilium agent

## Who is impacted and when? (Trigger Conditions)

_Affected versions_  
All Cilium versions

_Affected Images_  
All Cilium images

## Additional Resources

For more information, please refer to the following Official Cilium Documentation [here](https://docs.cilium.io/en/v1.12/operations/system_requirements)