---
title: Your Current Version of Filebeat is Unsupported
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

We strongly recommend upgrading your Filebeat version to the latest patch of one of the supported versions: `v8.x`  or `v7.17.x`.

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Running a Filebeat version that has reached end of support can lead to unintended behavior and functionality may not work as expected.

## Why does this exist? (Root Cause)

**_Please note that in this context, 'Unsupported' implies that Elastic will not maintain the Add-On once it reaches EOL_**

As per their [documentation](https://www.elastic.co/support/eol#:~:text=Elastic%20will%20provide%20maintenance)

> Elastic will provide maintenance (e.g., provide bug fixes or address security vulnerabilities) for each major release during the Maintenance Term either through a new minor release or a new maintenance release to the latest minor version. 

Additionally, the final minor version of the previous major version will also also supported.

## Additional Resources

For more information, please refer to [Elastic's Official Documentation.](https://www.elastic.co/support/eol)