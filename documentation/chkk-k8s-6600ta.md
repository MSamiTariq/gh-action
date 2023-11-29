---
title: Creating a policy using an incorrect schema will cause Kyverno to go into CrashLoopBackoff
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Upgrade Kyverno to `v1.10.1` or greater by following the instructions defined in the official Kyverno documentation [here](https://kyverno.io/docs/installation/upgrading/).

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

The impact of Kyverno panicking in a Kubernetes cluster includes disruptions in policy enforcement, potential violations, increased operational challenges, potential instability, security vulnerabilities, and possible disruptions in applications or services due to non-compliant resources - leading to potential availability issues.

## Why does this exist? (Root Cause)

This defect exists due to a bug in the code where errors related to type conversion were not being handled properly.

## Who is impacted and when? (Trigger Conditions)

Kyverno versions `≥ 1.3.0` and versions `< v1.10.1` will have this risk.

## Additional Resources

For more information, please refer to 

1. [Github Issue](https://github.com/kyverno/kyverno/issues/6556)
2. [PR that fixed this issue](https://github.com/kyverno/kyverno/pull/6526)