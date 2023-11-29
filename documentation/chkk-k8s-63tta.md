---
title: Tiller (Helm v2) should not be deployed
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Go Tillerless and use Helm v3

```yaml sample-pod.yaml
apiVersion: v1
kind: Pod
metadata:
  name: frontend
spec:
  containers:
    name: app
-   image: tiller
```

## Why does this exist? (Root Cause)

Tiller comes with broad range of permissions to access Kubernete API server. Tiller usually needs admin privileges and creates escalation of privileges for users with minimum privileges to interact with the cluster as if they were cluster admins.

## Affected Components

Containers and initContainers

## Additional Resources

For more details, please refer to the [official Kubernetes documentation](https://helm.sh/docs/topics/v2_v3_migration/).

To learn more about using Helm v3, please refer to the official Helm documentation here: [Helm](https://helm.sh)