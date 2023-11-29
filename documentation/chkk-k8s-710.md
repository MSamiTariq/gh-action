---
title: All Cilium components should run the same version
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Upgrade all components together from one stable release to another.

For example

Cilium Agent `v1.9.18` will **WORK**  with Cilium Operator `v1.9.18`  
Cilium Agent `v1.8.18` will **WORK** with Cilium Operator `v1.8.18`  
Cilium Agent `v1.8.18` will **NOT WORK** with Cilium Operator `v1.9.18`

Refer to official documentation for more [information around upgrades](https://docs.cilium.io/en/stable/operations/upgrade/) 

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Mismatched Cilium Operator and Agent versions is not a supported configuration and can lead to unexpected, untested behavior.

## Why does this exist? (Root Cause)

All Cilium components should run the same version during normal operation. Upgrading just one of them (e.g., upgrading the agent without upgrading the operator) could result in an unexpected cluster behavior.

## Who is impacted and when? (Trigger Conditions)

_Affected versions_  
All Cilium versions

_Affected Images_  
All Cilium images

## Additional Resources

For more details please refer to the official [Cilium documentation](https://docs.cilium.io/en/v1.12/operations/upgrade/#upgrading-cilium)