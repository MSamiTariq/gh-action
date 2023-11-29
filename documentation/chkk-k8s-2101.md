---
title: Your Current Version of AWS EBS CSI Driver is Unsupported
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

We strongly recommend upgrading your AWS EBS CSI Driver version to one of the supported minor versions: `v1.24` or `v1.25` . 

You may have [deployed the EBS CSI driver](https://github.com/kubernetes-sigs/aws-ebs-csi-driver/blob/master/docs/install.md#deploy-driver) via Kustomize, Helm, or as an Amazon EKS managed Add-On.

Depending upon your mode of installation you can follow these upgrade instructions 

**Amazon EKS managed Add-On**

To update Amazon EBS CSI on an existing cluster, you must initiate the update and then Amazon EKS updates the Add-On for you.

For example:

```bash shell
eksctl update addon --name aws-ebs-csi-driver --version <version>  --cluster <your cluster name> --force
```

More details can be found here: [Official AWS Documentation](https://docs.aws.amazon.com/eks/latest/userguide/managing-ebs-csi.html).

_Note: If you remove the --force option and any of the Amazon EKS Add-On settings conflict with your existing settings, then updating the Amazon EKS add-on fails, and you receive an error message to help you resolve the conflict. Before specifying this option, make sure that the Amazon EKS add-on doesn't manage settings that you need to manage, because those settings are overwritten with this option._

**Helm**

Add the aws-ebs-csi-driver Helm repository. (It should already be added)

```bash shell
helm repo add aws-ebs-csi-driver https://kubernetes-sigs.github.io/aws-ebs-csi-driver
helm repo update
```

Install the latest release of the driver.

_Please make sure to use your existing values file if you have made changes to the default config and supply it as an argument _

```bash shell
helm upgrade aws-ebs-csi-driver \
    --namespace <your namespace> \
    aws-ebs-csi-driver/aws-ebs-csi-driver \
    -f <path/to/value.yaml>
```

_Make sure you review the [configuration values](https://github.com/kubernetes-sigs/aws-ebs-csi-driver/blob/master/charts/aws-ebs-csi-driver/values.yaml) for the Helm chart. For each container (including the controller, node, and sidecars), there is an additionalArgs that accepts arguments that are not explicitly specified, such as --retry-interval-start, --retry-interval-max and --timeout that provisioner and attacher provides, or --kube-api-burst, --kube-api-qps etc._

**Kustomize**

_If you have made changes to the default config please make sure to incorporate them in the Yaml file before applying the changes_

```bash shell
kubectl apply -k "github.com/kubernetes-sigs/aws-ebs-csi-driver/deploy/kubernetes/overlays/stable/?ref=release-1.23"
```

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Running an AWS EBS CSI Driver version that has reached end of support can lead to unintended behavior and functionality may not work as expected.

## Why does this exist? (Root Cause)

As per the documentation,

> Support will be provided for the latest version and one prior version. Bugs or vulnerabilities found in the latest version will be backported to the previous release.

## Additional Resources

For more information, please refer to the following:

1. [AWS EBS CSI Driver Github Readme](https://github.com/kubernetes-sigs/aws-ebs-csi-driver#support)
2. [AWS EBS CSI Driver Official Documentation](https://docs.aws.amazon.com/eks/latest/userguide/ebs-csi.html)