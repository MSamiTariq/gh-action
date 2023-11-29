---
title: The support for wildcard queries has been removed in CoreDNS v1.9
category: 655c49ff76fdad0024723139
---

[block:api-header]
{
  "title": "How to fix it, long-term fix? (Remediation)"
}
[/block]
There is no remediation or long-term fix for this Availability Risk.
[block:api-header]
{
  "title": "How to fix it, short-term workaround? (Mitigation)"
}
[/block]
There is no mitigation or workaround for this Availability Risk.
[block:api-header]
{
  "title": "What is the impact? (Availability Impact)"
}
[/block]
The removal of wildcard queries means that, from v1.9 onwards, wildcards will not work with query labels that previously supported their use. These labels are as follows:

1. _endpoint_ in an `A` record request: _endpoint_.service.namespace.svc.zone
2. _service_ in an `A` record request: _service_.namespace.svc.zone
3. _namespace_ in an `A` record request: service._namespace_.svc.zone
4. _port and/or protocol_ in an `SRV` request: \_\_port\_.\_\_protocol\_.service.namespace.svc.zone
[block:api-header]
{
  "title": "Why does this exist? (Root Cause)"
}
[/block]
This change was implemented due to the vulnerability that the wildcard feature in CoreDNS's Kubernetes plugin presents. This vulnerability allowed unwanted access to sensitive information like the list of services, namespaces, and endpoint IPs in environments like Kubernetes. Thus this raised concerns about running untrusted code in a cluster in case that code executes lookups against CoreDNS.
[block:api-header]
{
  "title": "Additional Resources"
}
[/block]
For more information, see:
1. [GIthub Issue](https://github.com/coredns/coredns/issues/4984)
2. [The PR that fixed this issue](https://github.com/coredns/coredns/pull/5019)