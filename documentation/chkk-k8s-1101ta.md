---
title: Running ExternalDNS on Unsupported Architecture
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Use ExternalDNS with the supported architecture as specified by the following table:

| ExternalDNS | \< 0.7.5 | >= 0.7.5 |
| :---------- | :------- | :------- |
| amd64       | ✅        | ✅        |
| arm32       | ❌        | ✅        |
| arm64       | ❌        | ✅        |

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Running External DNS on an unsupported architecture can lead to failures.

## Why does this exist? (Root Cause)

ExternalDNS supports specific architectures depending on the version of ExternalDNS being used. This is summarized using the following table:

| ExternalDNS | \< 0.7.5 | >= 0.7.5 |
| :---------- | :------- | :------- |
| amd64       | ✅        | ✅        |
| arm32       | ❌        | ✅        |
| arm64       | ❌        | ✅        |

## Additional Resources

For more details please refer to the official [ExternalDNS documentation](https://github.com/kubernetes-sigs/external-dns/blob/master/docs/faq.md#which-architectures-are-supported).