---
title: CoreDNS tls plugin not configured for DNS over HTTPS will result in hard failure of the CoreDNS instance
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Add and configure the CoreDNS tls plugin. For more information, click [here](https://coredns.io/plugins/tls/).

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

When using HTTPS endpoints without the `tls` plugin configured and added, CoreDNS will error out and exit. This will result in name resolution errors and downtime.

## Why does this exist? (Root Cause)

CoreDNS `tls` plugin not configured for DNS over HTTPS will result in hard failure of the CoreDNS instance.

## Who is impacted and when? (Trigger Conditions)

_Affected Versions_  
All version of CoreDNS contain this Latent Availability Risk.

_Affected Images_  
Container images for CoreDNS are affected.

## Additional Resources

For more information, please refer to 

1. [Github Issue](https://github.com/coredns/coredns/pull/4162)

2. [CoreDNS Documenation](https://coredns.io/plugins/kubernetes/)