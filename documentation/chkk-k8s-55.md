---
title: Prefer using secrets as files over secrets as environment variables
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Do not set secrets as environment variables. Use secrets as files with defined file permissions.

```yaml valueFrom
apiVersion: v1
kind: Pod
metadata:
  name: test
spec:
  containers:
  - name: app
    image: images.my-company.example/app:v4
    env:
      - name: <env name>
        valueFrom:
-         secretKeyRef:
-           name: <secret key name>
-           key: <secret key>
```
```yaml envFrom
apiVersion: v1
kind: Pod
metadata:
  name: test
spec:
  containers:
    - name: app
      image: images.my-company.example/app:v4
      envFrom:
-     - secretRef:
-         name: <secret name>
```

## Why does this exist? (Root Cause)

Saving secrets as environment variables allows all processes running in a container to access this information. This violates the principle of least privilege.

## Affected Components

Containers and initContainers

## Additional Resources

For more details, please refer to the [official Kubernetes documentation](https://kubernetes.io/docs/concepts/configuration/secret/)