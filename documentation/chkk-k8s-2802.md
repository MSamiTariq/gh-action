---
title: Kubernetes External Secrets has reached End of Life
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

It is recommended to install the latest supported version of [External Secrets Operator](https://github.com/external-secrets/external-secrets) which is the successor to Kubernetes External Secrets, and an actively maintained Add-On.

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Kubernetes External Secrets is no longer actively maintained. As a result, relying on Kubernetes External Secrets may lead to compatibility issues and a potential lack of support for bug fixes and security patches.

## Why does this exist? (Root Cause)

Due to a lack of dedicated maintainers, Kubernetes External Secrets operated with limited support. Couple that with technical issues and obsolete dependencies arising from a large amount of tech debt, continuing to support KES would’ve been expensive in terms of time and resources. Thus, the decision was taken to deprecate the repository, and the Add-On, in favour of External Secrets Operator which had better documentation, better configuration possibilities, and used modern dependencies.

## Additional Resources

- [Kubernetes External Secrets Deprecation Notice](https://github.com/external-secrets/kubernetes-external-secrets/issues/864)
- [Kubernetes Secrets Operator Documentation](https://external-secrets.io/latest/introduction/overview/)
- [Official tool from the maintainers to help migrate from Kubernetes External Secrets to External Secrets Operator](https://github.com/external-secrets/kes-to-eso)