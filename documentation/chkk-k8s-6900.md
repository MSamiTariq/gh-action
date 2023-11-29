---
title: Unsupported version of Kiali
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Upgrade Kiali to a supported version. Supported versions for Kiali are the versions compatible with the currently supported versions of Istio. See the following table for currently supported versions of Istio and their correspondingly  compatible versions of Kiali.

| Istio Version | Compatible Kiali Versions | Notes                                         |
| :-----------: | :-----------------------: | --------------------------------------------- |
|     `1.19`    |          `1.72.0`         |                                               |
|     `1.18`    |    `1.67.0` - `1.73.0`    |                                               |
|     `1.17`    |    `1.63.2` - `1.66.1`    | Avoid `1.63.0`, `1.63.1` due to a regression. |
|   \< `1.16`   |       Out of Support      |                                               |

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Running an unsupported version of Kiali will lead to unintended behavior and functionality may not work as expected.

## Why does this exist? (Root Cause)

Kiali only supports versions that are compatible with the currently supported versions of Istio.

## Additional Resources

For more details, please refer to the official [Version Compatibility Table For Istio and Kiali](https://kiali.io/docs/installation/installation-guide/prerequisites/#version-compatibility:~:text=Supported%20Kiali%20versions%20include%20only%20the%20Kiali%20versions%20associated%20with%20supported%20Istio%20versions.)