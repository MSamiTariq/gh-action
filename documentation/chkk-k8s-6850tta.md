---
title: Unsupported version of Keycloak
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Upgrade your Keycloak version to the currently supporter major.minor version: `v22.0.x`.

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Running a Keycloak version that has reached end of support can lead to unintended behavior and functionality may not work as expected.

## Why does this exist? (Root Cause)

Keycloak supports the latest major.minor release at any given time. An outdated version of Keycloak will not receive security updates or technical support, and may cause your software to have incompatibilities leading to unknown behavior.

## Additional Resources

For more information, please refer to:

- [Official support policy](https://github.com/keycloak/keycloak/security/policy#supported-versions)