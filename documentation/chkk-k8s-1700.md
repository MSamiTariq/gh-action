---
title: FluentD deployed on a Node running an unsupported Operating System Image
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

We strongly recommend deploying FluentD on a Node running an OS Image supported by FluentD.

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Running FluentD on a Node with an unsupported OS Image will lead to an unintended behavior and functionality may not work as expected.

## Why does this exist? (Root Cause)

FluentD supports installation only on the specific operating systems as listed below

[block:html]
{
  "html": "<div style=\"padding-left:50px\">\n  <ul>\n    <li>Debian</li>\n    <li>Ubuntu</li>\n    <li>RHEL</li>\n    <li>CentOS</li>\n    <li>Amazon Linux</li>\n    <li>MacOS</li>\n    <li>Windows</li>\n  </ul>\n</div>"
}
[/block]

## Additional Resources

For more information see the FluentD documentation: [FluentD Documentation](https://www.fluentd.org/download)