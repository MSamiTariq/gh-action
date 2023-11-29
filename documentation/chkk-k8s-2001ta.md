---
title: ArgoCD server login hangs up if ArgoCD server is configured behind a LoadBalancer routing over HTTP1
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Step 1: Install ArgoCD CLI version >= `v2.4.12`

```text Linux
$VERSION=v2.4.12
$curl -sSL -o /usr/local/bin/argocd https://github.com/argoproj/argo-cd/releases/download/$VERSION/argocd-linux-amd64
$chmod +x /usr/local/bin/argocd
```
```text MacOS
$brew install argocd@2.4.12
```

Step 2: Apply argocd manifest to k8s cluster (>= `v2.4.12`)

```text kubectl
$kubectl create namespace argocd
$kubectl apply -n argocd -f \ https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/core-install.yaml
```

Step 3: Login to argocd-server

```text bash
$argocd login <server> --skip-test-tls --grpc-web
```

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Configuring argocd-server behind a LoadBalancer that routes over HTTP1 can result in the argocd login <server> command to hang up thereby resulting in the inability to setup or update the ArgoCD configuration.

## Why does this exist? (Root Cause)

In ArgoCD, running the argocd login <server> command initiates a TLS Test that expects gRPC over HTTP2. If the argocd-server is configured behind a LoadBalancer using HTTP1, the argocd login expects the –grpc-web flag to proxy gRPC over HTTP1 however, the login function does not change its behavior based on the –grpc-web flag. This will cause a failure if the LoadBalancer expects a call over HTTP1.

## Who is impacted and when? (Trigger Conditions)

Using ArgoCD versions less than `v2.4.12` and proxying argocd-server behind a HTTP1 LoadBalancer can trigger this Latent Availability Risk.

_Affected Versions_  
\< `v2.4.12`

_Affected Images_  
quay.io/argoproj/argocd

## Additional Resources

Details of the exact github issue can be found below  
[Issue Link](https://github.com/argoproj/argo-cd/issues/9679)  
[Fix link](https://github.com/argoproj/argo-cd/pull/10484)