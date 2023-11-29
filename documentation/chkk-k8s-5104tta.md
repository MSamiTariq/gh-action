---
title: Unsupported version of SonarQube
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Upgrade to one of the supported versions of SonarQube which currently are: `v9.9.x`and `v10.3.x`.

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Running a SonarQube version that has reached end of support can lead to unintended behavior and functionality may not work as expected.

## Why does this exist? (Root Cause)

SonarQube supports the latest major.minor release as well as the latest LTS release at any given time. An outdated version of SonarQube will not receive security updates or technical support, and may cause your software to have incompatibilities leading to unknown behavior.

## Additional Resources

For more information, please refer to:

- [Latest LTS version ](https://www.sonarsource.com/products/sonarqube/downloads/lts/)
- [SonarQube releases](https://github.com/SonarSource/sonarqube/releases)