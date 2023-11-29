---
title: Tiller Service (Helm v2) should not be deployed
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Go Tillerless and use Helm v3.

```yaml
-- apiVersion: v1
-  kind: Service
-  metadata:
-    labels:
-      app: helm
-      name: tiller
-    name: tiller-deploy
-    namespace: kube-system
-  spec:
-    ports:
-    - name: tiller
-      port: 44134
-      protocol: TCP
-      targetPort: tiller
-    selector:
-      app: helm
-      name: tiller
-    type: ClusterIP
```

## How to fix it, short-term workaround? (Mitigation)

Replace Helm v2 with v3 in your cluster deployment.

## What is the impact? (Availability Impact)

Tiller violates the principle of least privilege as it comes with a broad range of permissions to access Kubernetes API server making it susceptible to potential attacks by malicious user processes.

## Why does this exist? (Root Cause)

Helm maintainers are aware of the vulnerabilities that having a server side for Helm causes, so in Helm v3, they got rid of Tiller.

## Who is impacted and when? (Trigger Conditions)

_Affected Versions_  
All EKS clusters or Kubernetes clusters using Tiller v2 deployment.

_Affected Images_  
All container images referencing Tiller v2 version.

## Additional Resources

To get more details on removal of Tiller please refer to the [official documentation of Helm](https://v3.helm.sh/docs/faq/changes_since_helm2/#removal-of-tiller)