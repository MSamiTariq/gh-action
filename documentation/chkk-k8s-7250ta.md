---
title: Argo CD Notifications has reached End of Life
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

It is recommended to utilize Argo CD's built-in notifications controller instead of Argo CD Notifications. This ensures that you are using the officially supported functionality provided by Argo CD, reducing the risk of compatibility issues and ensuring access to bug fixes and security patches. Starting from [version v2.3](https://argo-cd.readthedocs.io/en/stable/operator-manual/upgrading/2.2-2.3/), Argo CD notifications were integrated into Argo CD itself. Therefore, it is important to ensure that you are running Argo CD version greater than 2.3 to take advantage of this built-in functionality.

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Argo CD Notifications is no longer actively maintained. As a result, relying on Argo CD Notifications may lead to compatibility issues with future versions of Argo CD and potential lack of support for bug fixes and security patches.

## Why does this exist? (Root Cause)

Argo CD Notifications has been integrated into Argo CD itself. The built-in notifications controller continuously monitors Argo CD Notifications applications and provides a flexible way to notify users about important changes in the application state.

## Additional Resources

- [Argo CD Notifications deprecation notice](https://github.com/argoproj-labs/argocd-notifications#argo-cd-notifications-is-now-part-of-argo-cd)
- [Migrating from Argo CD Notifications to Argo CD's built in notifications controller ](https://argo-cd.readthedocs.io/en/stable/operator-manual/upgrading/2.2-2.3/)