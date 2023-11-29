---
title: Cortex requires at least docker v19.3.6
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

We recommend upgrading docker container runtime to at least `v19.3.6` for the node(s) running cortex.

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

According to the official system requirements, cortex requires at least docker `v19.3.6`. Trying to run cortex on an older docker version might result in unintended behavior.

## Why does this exist? (Root Cause)

cortex recommends using a docker container runtime version for which it is supported.

## Additional Resources

For more details, please refer to the official [cortex documentation](https://cognitivescale.github.io/cortex-charts/docs/cluster-sizing)