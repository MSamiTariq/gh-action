---
title: Unsupported version of Node Feature Discovery
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

We strongly recommend upgrading Node Feature Discovery to one of the following supported versions: `0.14.x` and `0.13.x`.

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Running a Node Feature Discovery version that has reached end of support can lead to unintended behavior and functionality may not work as expected.

## Why does this exist? (Root Cause)

Node Feature Discovery's maintainers support N-1 minor releases at any time as seen in [this GitHub issue](https://github.com/kubernetes-sigs/node-feature-discovery/issues/1131). This means, only the latest two releases will receive security updates, bug fixes and important features.

## Additional Resources

For more details, please refer to the following:

- [Supported versions documentation](https://github.com/kubernetes-sigs/node-feature-discovery/blob/master/docs/reference/versions.md)

  Documentation for supported release.

- [v0.13.x](https://kubernetes-sigs.github.io/node-feature-discovery/v0.13/get-started/index.html)

- [v0.14.x](https://kubernetes-sigs.github.io/node-feature-discovery/v0.14/get-started/index.html)