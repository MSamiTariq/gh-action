---
title: Your current version of Redis OSS has reached end-of-life.
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Upgrade Redis OSS to a supported version. The following table depicts recent releases and their support status

| Release            | Support | Latest    |
| :----------------- | :------ | :-------- |
| `v7.2`             | Yes     | `v7.2.1`  |
| `v7.0`             | Yes     | `v7.0.12` |
| `v6.2`             | Yes     | `v6.2.13` |
| `v6.0`             | No      | `v6.0.20` |
| `v5.0` and earlier | No      | `v5.0.14` |

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

The version of Redis OSS you are running has reached end-of-life, which means you cannot receive security updates, technical support and the software may have incompatibilities leading to unknown behavior. 

## Why does this exist? (Root Cause)

Newer versions of Redis OSS released by the Redis OSS community are tried and tested against various vulnerabilities and contain new features for their users, and are mostly backwards compatible. Hence, support for older versions is dropped. 

The latest stable release is always fully supported and maintained. Two additional versions receive maintenance only, meaning that only fixes for critical bugs and major security issues are committed and released as patches:

- The previous minor version of the latest stable release.
- The previous stable major release.

## Additional Resources

For more information see

- [Redis' Version Support Policy](https://redis.io/docs/about/releases/#:~:text=The%20latest%20stable,stable%20major%20release.)
- [Redis' release cycle](https://redis.io/docs/about/releases/)
- [Redis' GitHub Releases page](https://github.com/redis/redis/releases)