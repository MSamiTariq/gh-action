---
title: CAP_SYS_ADMIN privileges must be granted to cilium-agent to interact with the Linux kernel
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Run cilium-agent as root and/or as a privileged container

```yaml
image: quay.io/cilium/cilium:v1.9.18
imagePullPolicy: IfNotPresent
securityContext:
+   privileged: true

#  Or

image: quay.io/cilium/cilium:v1.9.18
imagePullPolicy: IfNotPresent
securityContext:
    capabilities:
        Add:
    +   - CAP_SYS_ADMIN
```

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Insufficient privileges will not let Cilium Agent  perform networking tasks on host machines which  can lead to undesired behavior.

## Why does this exist? (Root Cause)

Cilium interacts with the Linux kernel to install eBPF programs which will then perform networking tasks and implement security rules. In order to install eBPF programs system-wide, CAP_SYS_ADMIN privileges are required. These privileges must be granted to cilium-agent.

## Who is impacted and when? (Trigger Conditions)

_Affected versions_  
All Cilium versions

_Affected Images_  
All Cilium images

## Additional Resources

For more information see: [Cilium's system requirements](https://docs.cilium.io/en/stable/operations/system_requirements/#privileges) regarding Privileges