---
title: Allow Service manifest for gateway to support same port with different protocols
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Upgrade Istio to `v1.12.0-alpha.1` or above to apply the available patch. To upgrade your version of Istio, please follow the steps given in the Official Istio Documentation [here](https://istio.io/latest/docs/setup/upgrade/)

## How to fix it, short-term workaround? (Mitigation)

Avoid specifying multiple protocols for the same service port.

## What is the impact? (Availability Impact)

The unintended port overwrite by the last specified protocol can lead to unexpected behavior where the existing traffic flows in the cluster are disrupted.

## Why does this exist? (Root Cause)

In Istio versions `v1.11.2` and earlier, the same service port cannot be configured with different protocols. Kubernetes will apply the last specified protocol, overwriting the previous protocols in that order.

## Who is impacted and when? (Trigger Conditions)

_Affected Versions_  
All EKS clusters or Kubernetes clusters using Istio versions `v1.11.2` and earlier.

_Affected Images_  
The container image tags for Istio with version `v1.11.2` and below are affected.

## Additional Resources

Details of the exact Github issue can be found [here](https://github.com/istio/istio/issues/33841).