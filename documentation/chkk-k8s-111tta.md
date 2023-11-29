---
title: Restrict Istio discovery container to set root file system as read-only
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Set `readOnlyRootFilesystem` as `True` in `spec.containers.[].securityContext` for Istio discovery container.

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: istiod
  namespace: istio-system
  labels:
    app: istiod
    istio.io/rev: default
    install.operator.istio.io/owning-resource: unknown
    operator.istio.io/component: "Pilot"
    istio: pilot
    release: istio
spec:
  selector:
    matchLabels:
      istio: pilot
  template:
    metadata:
      labels:
        app: istiod
        istio.io/rev: default
        install.operator.istio.io/owning-resource: unknown
        sidecar.istio.io/inject: "false"
        operator.istio.io/component: "Pilot"
        istio: pilot
      annotations:
        prometheus.io/port: "15014"
        prometheus.io/scrape: "true"
        sidecar.istio.io/inject: "false"
    spec:
      serviceAccountName: istiod
      securityContext:
        fsGroup: 1337
      containers:
        - name: discovery
          image: "gcr.io/istio-testing/pilot:latest"
          args:
          - "discovery"
          - --monitoringAddr=:15014
          - --log_output_level=default:info
          - --domain
          - cluster.local
          - --keepaliveMaxServerConnectionAge
          - "30m"
          ports:
          - containerPort: 8080
            protocol: TCP
          - containerPort: 15010
            protocol: TCP
          - containerPort: 15017
            protocol: TCP
          resources:
            requests:
              cpu: 500m
              memory: 2048Mi
          securityContext:
+            readOnlyRootFilesystem: true
            runAsUser: 1337
            runAsGroup: 1337
            runAsNonRoot: true
            capabilities:
              drop:
              - ALL
```
```yaml Terraform
# coming soon
```
```yaml Pulumi
# coming soon
```

For more details on configuring the securityContext for a Pod or container, please refer to the official Kubernetes documentation here:  
[K8s-Pod-Security-Context](https://kubernetes.io/docs/tasks/configure-pod-container/security-context/)

## How to fix it, short-term workaround? (Mitigation)

Avoid setting `readOnlyRootFilesystem` as `False` for any container unless absolutely required.

## What is the impact? (Availability Impact)

Root file system without read-only permission violates the principle of least privilege, making it possible to exploit potential vulnerabilities.

## Why does this exist? (Root Cause)

Setting security context as read-only for root filesystem improves the security posture and follows the principle of least privilege.

## Who is impacted and when? (Trigger Conditions)

_Affected Versions_  
All EKS clusters or Kubernetes clusters using any version of Istio.

_Affected Images_  
All container image tags for Istio are affected.

## Additional Resources

Details of the exact github issue can be found [here](https://github.com/istio/istio/issues/33999)