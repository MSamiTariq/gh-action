---
title: TLS Certificate Mismatch Leads to Kyverno Webhook Failures
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Upgrade Kyverno to `v1.11.0` or greater.

## How to fix it, short-term workaround? (Mitigation)

Redeploy the same Kyverno version. 

## What is the impact? (Availability Impact)

A webhook failure in Kyverno renders Kyverno non-functional and compromises the cluster's integrity. This can potentially lead to security vulnerabilities, as well as service interruptions and outages, stemming from unexpected network behavior due to the lack of policy enforcement.

## Why does this exist? (Root Cause)

When the CA certificate is deleted, the TLS certificate is not renewed. This leads to mismatched certificate chain since the server certificate cannot be verified or validated as legitimate by the Kubernetes API server. This issue results in webhook failures because the Kyverno admission endpoint becomes unavailable.

## Who is impacted and when? (Trigger Conditions)

Kyverno versions `≥ 1.8.0` and versions `< v1.11.0` will have this risk.

## Additional Resources

For more information, please refer to 

1. [Github Issue](https://github.com/kyverno/kyverno/issues/8074)
2. [PR that fixed this issue](https://github.com/kyverno/kyverno/pull/8114)