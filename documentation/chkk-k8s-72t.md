---
title: CronJob v1beta1 Deprecation
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Migrate manifests and API clients to use the `batch/v1` API version, available since `v1.21`.  
All existing persisted objects are accessible via the new API  
No notable changes

```yaml sample-cronjob.yaml
- apiVersion: batch/v1beta1
+ apiVersion: batch/v1
kind: CronJob
metadata:
  name: hello
spec:
  schedule: "*/1 * * * *"
  jobTemplate:
    spec:
      template:
        metadata:
          labels:
            app: test-cronjob
        spec:
          containers:
          - name: hello
            image: test/image
          restartPolicy: OnFailure
```

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## Why does this exist? (Root Cause)

The batch/v1beta1 API version of CronJob will no longer be served in `v1.25`.

## Additional Resources

For more details, please refer to the official [Kubernetes documentation](https://kubernetes.io/docs/reference/using-api/deprecation-guide/#cronjob-v125)