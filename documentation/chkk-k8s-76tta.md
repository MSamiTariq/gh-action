---
title: Event v1beta1 Deprecation
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Migrate manifests and API clients to use the `events.k8s.io/v1` API version, available since `v1.19`.  
All existing persisted objects are accessible via the new API  
Notable changes in `events.k8s.io/v1`:

- `type` is limited to `Normal` and `Warning`
- `involvedObject` is renamed to `regarding`
- `action`, `reason`, `reportingController`, and `reportingInstance` are required when creating new **events.k8s.io/v1 Events**
- use `eventTime` instead of the deprecated `firstTimestamp` field (which is renamed to `deprecatedFirstTimestamp` and not permitted in new **events.k8s.io/v1 Events**)
- use `series.lastObservedTime` instead of the deprecated `lastTimestamp` field (which is renamed to `deprecatedLastTimestamp` and not permitted in new **events.k8s.io/v1 Events**)
- use `series.count` instead of the deprecated `count` field (which is renamed to `deprecatedCount` and not permitted in new **events.k8s.io/v1 Events**)
- use `reportingController` instead of the deprecated `source.component` field (which is renamed to `deprecatedSource.component` and not permitted in new **events.k8s.io/v1** Events)
- use `reportingInstance` instead of the deprecated `source.host` field (which is renamed to `deprecatedSource.host` and not permitted in new **events.k8s.io/v1** Events) 

```yaml sample-event.yaml
+ apiVersion: events.k8s.io/v1
- apiVersion: events.k8s.io/v1beta1
kind: Event
action: "26"
eventTime: "2600-06-10T04:50:19.358488Z"
metadata:
  name: "Test"
note: "40"
reason: "27"
regarding:
  apiVersion: "31"
  fieldPath: "33"
  kind: "28"
  name: "30"
  namespace: "29"
  resourceVersion: "32"
related:
  apiVersion: "37"
  fieldPath: "39"
  kind: "34"
  name: "36"
  namespace: "35"
  resourceVersion: "38"
reportingController: "24"
reportingInstance: "25"
series:
  count: 2114329341
  lastObservedTime: "1999-07-03T22:31:10.529225Z"
type: "41"
```

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## Why does this exist? (Root Cause)

The `events.k8s.io/v1beta1` API version of Event will no longer be served in `v1.25`.

## Additional resources

For more details on the deprecation of `events.k8s.io/v1beta1`, please refer to the official Kubernetes documentation here: [K8s-Deprecated-API-Migration-Guide](https://kubernetes.io/docs/reference/using-api/deprecation-guide/#event-v125)