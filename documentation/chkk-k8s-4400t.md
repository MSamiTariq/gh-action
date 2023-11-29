---
title: AWS IAM Authenticator for EKS v1.25 requires macros enclosed in double quotes in the aws-auth ConfigMap
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

You must add double quotation marks before and after curly braces in the `aws-auth` ConfigMap (found in the `kube-system` namespace) if a YAML value starts with a macro (i.e., the first character is a curly brace). For example, if you set your username to `{{SessionName}}` in your `aws-auth` ConfigMap without any double quotes, like:

```yaml
username: {{SessionName}}
```

then you must update it to `"{{SessionName}}"`.

```yaml
username: "{{SessionName}}"
```

 However, if the first character is not a curly brace, like:

```yaml
username: admin:{{SessionName}}
```

then no action is required.

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Including macros without double quotes can possibly lead to authentication failures in your cluster.

## Why does this exist? (Root Cause)

This is required to ensure accurate parsing of the `aws-auth` ConfigMap by aws-iam-authenticator `v0.6.3` used in Amazon EKS `v1.25`.

## Who is impacted and when? (Trigger Conditions)

_Affected Versions_  
All EKS clusters greater than or equal to `v1.25.0` contain this Latent Availability Risk.

## Additional Resources

For more information see “Updates to AWS IAM Authentication” in the blog post: [Amazon EKS now supports Kubernetes version 1.25](https://aws.amazon.com/blogs/containers/amazon-eks-now-supports-kubernetes-version-1-25/)