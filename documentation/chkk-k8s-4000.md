---
title: k8s.gcr.io Image Registry Will Be Frozen From the 3rd of April 2023
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Make sure your cluster does not have dependencies on the old image registry. You can run the following command to list images used by pods

```shell
kubectl get pods --all-namespaces -o jsonpath="{.items[*].spec.containers[*].image}" |\
tr -s '[[:space:]]' '\n' |\
sort |\
uniq -c
```

Replace the image strings with `k8s.gcr.io` to `registry.k8s.io`. Furthermore, you will need to update your manifests and Helm charts to use the new registry.

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Starting from `v1.25`, Kubernetes (and its sub-projects) releases are no longer published to `k8s.gcr.io` but only to `registry.k8s.io`. Those who have strict access policies limited to `k8s.gcr.io` should mirror the release images to a private registry, as image pulls will not function anymore. Patch releases for 1.24, 1.25, and 1.26 are no longer be published to the old registry since April 2023. The default image registry is now set to `registry.k8s.io`, and setting it to `k8s.gcr.io` will fail for new releases after April 3rd, 2023.

## Why does this exist? (Root Cause)

The Kubernetes project's custom GCR domain, `k8s.gcr.io`, has been used successfully but other cloud providers and vendors now want to host images to enhance user experience and reduce costs. The new registry, `registry.k8s.io`, will distribute the load between Google and Amazon, and potentially other providers in the future. This will improve user experience by enabling faster downloads due to closer servers and reduce costs associated with egress bandwidth from GCR.

See this blog post by Kubernetes about `registry.k8s.io` general availability: [registry.k8s.io: faster, cheaper and Generally Available (GA) | Kubernetes](https://kubernetes.io/blog/2022/11/28/registry-k8s-io-faster-cheaper-ga/) 

## Timeline of the changes

- `k8s.gcr.io` will be frozen on the 3rd of April 2023
- 1.27 is expected to be released on the 12th of April 2023
- The last 1.23 release on `k8s.gcr.io` will be `1.23.18` (1.23 goes end-of-life before the freeze)
- The last 1.24 release on `k8s.gcr.io` will be `1.24.12`
- The last 1.25 release on `k8s.gcr.io` will be `1.25.8`
- The last 1.26 release on `k8s.gcr.io` will be `1.26.3`

## Additional Resources

For more information see the following blog posts

- [k8s.gcr.io Image Registry Will Be Frozen From the 3rd of April 2023 | Kubernetes](https://kubernetes.io/blog/2023/02/06/k8s-gcr-io-freeze-announcement/)
- [registry.k8s.io: faster, cheaper and Generally Available (GA) | Kubernetes](https://kubernetes.io/blog/2022/11/28/registry-k8s-io-faster-cheaper-ga/)