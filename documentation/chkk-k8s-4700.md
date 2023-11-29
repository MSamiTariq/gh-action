---
title: Spire server crashes on database operation failure
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Upgrade to Spire versions >= `v1.6.0`

Please follow the [Quick start](https://spiffe.io/docs/latest/try/getting-started-k8s/) guide to learn more.

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Due to the crash in Spire server, the applications in your cluster signed by Spire will be unable to authenticate thereby rendering the Spire dependent applications unusable.

## Why does this exist? (Root Cause)

In Spire versions \< `v1.6.0`, in case of a failure in database operation, a nil context variable is returned. This context variable is subsequently used to fetch a logger. Since the context is nil, an attempt to access the logger results in a nil pointer dereference crashing the Spire server.

## Who is impacted and when? (Trigger Conditions)

Using Spire versions \< `v1.6.0` can trigger this Latent Availability Risk.

Affected versions  
All clusters using Spire versions less than `v1.6.0` contain this Latent Availability Risk.

Affected images  
spiffe/spire-server

## Additional Resources

 [Pull request that fixed the issue](https://github.com/spiffe/spire/pull/3829)

[Changelog for v1.6.0](https://github.com/spiffe/spire/blob/main/CHANGELOG.md#fixed-1)