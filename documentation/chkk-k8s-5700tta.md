---
title: Unsupported version of HashiCorp Consul
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

We strongly recommend upgrading HashiCorp Consul to a supported version. As per the [official documentation](https://developer.hashicorp.com/consul/docs/k8s/compatibility#supported-consul-and-kubernetes-versions), the three currently supported minor releases are: `1.3.x`, `1.2.x` and `1.1.x`.

Refer to the [official Consul upgrade guide](https://developer.hashicorp.com/consul/docs/k8s/upgrade) for more information.

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Running a HashiCorp Consul version that has reached end of support can lead to unintended behavior and functionality may not work as expected.

## Why does this exist? (Root Cause)

Hashicorp provides support for only the three latest minor releases of Consul.

## Additional Resources

For more details, please refer to [Official HashiCorp Consul Documentation](https://developer.hashicorp.com/consul/docs/k8s/compatibility#supported-consul-and-kubernetes-versions)