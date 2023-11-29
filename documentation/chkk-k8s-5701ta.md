---
title: The detected HashiCorp Consul version is not compatible with your Kubernetes version
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

We strongly recommend running a HashiCorp Consul version that is compatible with your Kubernetes version as shown within the following table:

| HashiCorp Consul-k8s Version | Compatible K8s Versions |
| ---------------------------- | ----------------------- |
| `v1.3.x`                     | `v1.25.x` - `v1.28.x`   |
| `v1.2.x`                     | `v1.24.x` - `v1.27.x`   |
| `v1.1.x`                     | `v1.23.x` - `v1.26.x`   |

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

HashiCorp Consul is not compatible by the Kubernetes version you are running, which means that the software may have incompatibilities leading to unknown behavior.

## Why does this exist? (Root Cause)

Each version of HashiCorp Consul-k8s has been tested with a range of specific Kubernetes versions which are considered as compatible and defined within the table above.

## Additional Resources

For more details, please refer to [Official HashiCorp Documentation](https://developer.hashicorp.com/consul/docs/k8s/compatibility#supported-consul-and-kubernetes-versions)