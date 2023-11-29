---
title: Configure Startup probes for containers that have unpredictable startup time
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Define the Startup probes at `.spec.containers[].startupProbe` for each container having an unpredictable startup time.

## How to fix it, short-term workaround? (Mitigation)

If the initialization time of your application is known, use `initialDelaySeconds` when configuring Liveness/Readiness probes.

## What is the impact? (Availability Impact)

Applications whose startup time is unpredictable can be interrupted from completing their initialization routines by any Liveness or Readiness probe, which may fail before allowing the application to become healthy.

## Why does this exist? (Root Cause)

Configure Startup probes to ensure your application with unpredictable startup time becomes healthy and functional before other probes become operational.

## Who is impacted and when? (Trigger Conditions)

_Affected Versions_  
All Kubernetes versions

_Affected Images_  
All images

## Additional Resources

For more details, please refer to the [official Kubernetes documentation](https://kubernetes.io/docs/tasks/configure-pod-container/configure-liveness-readiness-startup-probes/)