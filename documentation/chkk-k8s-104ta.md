---
title: Port exposed in a Service should not be bound to a localhost address
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

If the application is not required to be exposed to other pods, remove the port from the Service.

If the application is required to be exposed to other pods, there are two options:

- Update the application to bind to a network interface exposed to other pods. Generally, this means binding to `0.0.0.0` or `::`. For example, configure netcat to listen on `0.0.0.0` and port `26500` as shown below:

```yaml
---
apiVersion: apps/v1beta1
kind: Deployment
metadata:
  name: nc-pod
  labels:
    name: nc-pod
    app: nc-pod
    version: 0.1.0
spec:
  replicas: 1
  template:
    metadata:
      labels:
        app: nc-pod
        version: 0.1.0
    spec:
      containers:
        - name: nc-pod
          image: quay.io/samsung_cnct/nc-pod:latest
          env:
            - name: NC_CMD_ARGS
              value: "-n -k -v -l 0.0.0.0 26500"
          ports:
          - containerPort: 26500
---
apiVersion: v1
kind: Service
metadata:
  name: netcat
spec:
  ports:
  - port: 26500
    protocol: TCP
  selector:
    app: nc-pod
```

- Define a `Sidecar` configuration to customize the inbound networking configuration for the pod. For example, to configure the `8080` port to explicitly be sent to `localhost`:

```yaml
apiVersion: networking.istio.io/v1beta1
kind: Sidecar
metadata:
  name: ratings
spec:
  workloadSelector:
    labels:
      app: nc-pod
  ingress:
  - port:
      number: 8080
      protocol: HTTP
      name: http
    defaultEndpoint: 127.0.0.1:8080
```

For more details on setting up inbound forwarding with Istio, please refer to the official Istio documentation here:  
[Istio-Inbound-Forwarding-Configuration](https://istio.io/latest/news/releases/1.10.x/announcing-1.10/upgrade-notes/#inbound-forwarding-configuration)

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk Signature.

## What is the impact? (Availability Impact)

Applications relying on `localhost` being exposed externally by Istio may stop working

## Why does this exist? (Root Cause)

With Istio v1.10 and later, the default behavior of Inbound Forwarding has changed to forward requests as is, with out redirecting to `localhost`. As a result, in the older versions of Istio where applications rely on `localhost` being exposed externally by Istio may stop working.

## Who is impacted and when? (Trigger Conditions)

_Affected Versions_  
All EKS clusters or Kubernetes clusters using versions of Istio later than and including `v1.10`

_Affected Images_  
The container image tags for Istio later than and including `v1.10` are affected.

## Additional resources

More details can be found in the [upgrade notes](https://istio.io/latest/news/releases/1.10.x/announcing-1.10/upgrade-notes/#inbound-forwarding-configuration) for Istio `v1.10`