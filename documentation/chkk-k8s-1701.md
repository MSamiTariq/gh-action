---
title: Grafana deployed on a Node running an unsupported Operating System Image
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

We strongly recommend deploying Grafana on a Node running an OS Image supported by Grafana.

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Running Grafana on a Node with an unsupported OS Image will lead to an unintended behavior and functionality may not work as expected.

## Why does this exist? (Root Cause)

Grafana Supports installation only on the specific operating systems as listed below

[block:html]
{
  "html": "<div style=\"padding-left:50px\">\n  <ul>\n    <li>Debian</li>\n    <li>Ubuntu</li>\n    <li>RHEL</li>\n    <li>Fedora</li>\n    <li>SUSE/OpenSUSE</li>\n    <li>MacOS</li>\n    <li>Windows</li>\n    <li>Amazon Linux 2</li>\n  </ul>\n</div>"
}
[/block]

## Additional Resources

For more information see the Grafana documentation: [Grafana Documentation](https://grafana.com/docs/grafana/latest/setup-grafana/installation/#supported-operating-systems)