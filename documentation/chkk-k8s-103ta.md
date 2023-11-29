---
title: Ingress backend servicePort removal
category: 655c49ff76fdad0024723139
---

[block:api-header]
{
  "title": "How to fix it, long-term fix? (Remediation)"
}
[/block]
After upgrade, change to `service.port.number` if numeric, `service.port.name` if string
[block:code]
{
  "codes": [
    {
      "code": "apiVersion: networking.k8s.io/v1\nkind: Ingress\nmetadata:\n  name: test\nspec:\n  backend:\n    serviceName: test\n    - servicePort: 443\n    + service:\n    +   port:\n    +     number: 443\n  rules:\n  - host: test1\n    http:\n      paths:\n      - backend:\n          serviceName: test1\n          - servicePort: 443\n          + service:\n          +   port:\n          +     number: 443\n  - host: test2\n    http:\n      paths:\n      - backend:\n          serviceName: test2\n          - servicePort: 443\n          + service:\n          +   port:\n          +     number: 443",
      "language": "yaml",
      "name": "sample-ingress.yaml"
    }
  ]
}
[/block]
For more details on the deprecation of Ingress, please refer to the official Kubernetes documentation here: [K8s-Deprecated-API-Migration-Guide](https://kubernetes.io/docs/reference/using-api/deprecation-guide/)
[block:api-header]
{
  "title": "How to fix it, short-term workaround? (Mitigation)"
}
[/block]
There is no mitigation or workaround for this Availability Risk.
[block:api-header]
{
  "title": "Why does this exist? (Root Cause)"
}
[/block]
Ingress backend `servicePort` property has been removed in `networking.k8s.io/v1`.
[block:api-header]
{
  "title": "Additional Resources"
}
[/block]
For more details, please refer to the [official Kubernetes documentation ](https://kubernetes.io/docs/reference/using-api/deprecation-guide/#ingress-v122)