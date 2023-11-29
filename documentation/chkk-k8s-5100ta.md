---
title: Incompatible version of Kubernetes with SonarQube
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Upgrade your Kubernetes version to one of the officially supported Kubernetes versions i.e. n-2 or greater.

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Running SonarQube on an incompatible version of Kubernetes will lead to an unintended behavior and functionality may not work as expected.

## Why does this exist? (Root Cause)

SonarQube aligns its support for Kubernetes versions in accordance with the official Kubernetes support policy, specifically focusing on the two versions preceding the latest kubernetes minor release. This information is applicable exclusively to SonarQube's latest LTS release and subsequent versions as per [this thread](https://community.sonarsource.com/t/k8s-compatibility-for-sts-versions/91899) on SonarQube forums

## Additional Resources

For more information, please refer to the [Official SonarQube Documentation](https://docs.sonarqube.org/9.8/setup-and-upgrade/deploy-on-kubernetes/deploy-sonarqube-on-kubernetes/#kubernetes-environment-recommendations)