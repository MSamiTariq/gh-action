---
title: The Privileged Pod Security Policy cannot be used in combination with SonarQube
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Remove the privileged Pod Security Policy from your SonarQube container.

You can do so by referring to the following [Official Kubernetes guide](https://kubernetes.io/docs/tasks/configure-pod-container/security-context/).

For example:

```shell shel
securityContext:
          runAsUser: 1000
          privileged: true  //should not be present
```

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Running SonarQube with privileged permissions can lead to high severity issues including, but not limited to, unauthorized access, higher vulnerability to exploits, and confidentiality risks.

## Why does this exist? (Root Cause)

According to SonarQube's official documentation, the privileged Pod Security Policy is incompatible with SonarQube. An excerpt from the [official SonarQube documentation](https://docs.sonarqube.org/latest/setup-and-upgrade/deploy-on-kubernetes/deploy-sonarqube-on-kubernetes/) says:  

_The SonarQube images are currently intended to start as root in order to provision the PVC and drop to lower privileges after that._

## Who is impacted and when? (Trigger Conditions)

_Affected Versions_  
All SonarQube versions

## Additional Resources

For more information, please refer to [SonarQube Official Documentation](https://docs.sonarqube.org/latest/setup-and-upgrade/deploy-on-kubernetes/deploy-sonarqube-on-kubernetes/).