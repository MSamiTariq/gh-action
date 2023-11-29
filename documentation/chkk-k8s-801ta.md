---
title: A race condition in AWS Load Balancer Controller prevents Pod registration in Target Groups
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Upgrade to AWS Load Balancer Controller version `v2.4.1` or greater.

```yaml k8s manifest
# Update the image tag in your AWS load balancer controller deployment k8s manifest  

      containers:
      - args:
        - --cluster-name=your-cluster-name
        - --ingress-class=alb
        image: amazon/aws-alb-ingress-controller:v2.4.1
        
  # Change the image name in case ECR hosted image is used in your environment
```
```shell kubectl
kubectl set image deployment/aws-load-balancer-controller \
  controller=amazon/aws-alb-ingress-controller:v2.4.1 \
  -n kube-system
  
# Change the image name in case ECR hosted image is used in your environment
```
```yaml Terraform
# coming soon
```
```yaml Pulumi
# coming soon
```

## What is the impact? (Availability Impact)

All the pods failing the readiness gate will not receive traffic, causing downtime for an application--until the pods are deleted and recreated. 

## How to fix it, short-term workaround? (Mitigation)

Manually delete the application pods that are not in ready state to force them to be re-created and getting registered on the Target Group.

## Why does this exist? (Root Cause)

Updating an [IngressGroup](https://kubernetes-sigs.github.io/aws-load-balancer-controller/v2.2/guide/ingress/annotations/#ingressgroup) during a Deployment rollout can cause new pods to never register on the new [Target Group](https://docs.aws.amazon.com/elasticloadbalancing/latest/application/load-balancer-target-groups.html). This causes application downtime as pods' fail readiness, Deployment rollout is stalled, and traffic is not sent to the affected pods. 

## Who is impacted and when? (Trigger Conditions)

_Affected Versions_

All AWS Load Balancer Controller versions earlier than `v2.4.1` contain this Latent Availability Risk (LAR).

_Affected Images_

All image tags for AWS Load Balancer Controller version earlier than `v2.4.1` are affected.  

The official docker image name is `docker.io/amazon/aws-alb-ingress-controller:*`

`e.g docker.io/amazon/aws-alb-ingress-controller:2.4.0`

And ECR image name is `.amazonaws.com/amazon/aws-load-balancer-controller:`

`e.g 
*.dkr.ecr.us-west-2.amazonaws.com/amazon/aws-load-balancer-controller:v2.4.0`

## Additional Resources

The GitHub issues can be found [here](https://github.com/kubernetes-sigs/aws-load-balancer-controller/issues/1764) and [here](https://github.com/kubernetes-sigs/aws-load-balancer-controller/issues/2393)