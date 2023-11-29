---
title: Apache Airflow does not support the detected Kubernetes version
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Use a version of Apache Airflow that is supported for your version of Kubernetes.

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Running an unsupported version combination of Apache Airflow and Kubernetes can lead to unintended behavior and functionality may not work as expected.

## Why does this exist? (Root Cause)

Apache recommends using a Kubernetes control plane version for which Airflow is supported. Airflow follows the same support policy as Kubernetes which means that N-3 Kubernetes versions are supported.

As per Apache Airflow official documentation. 

_As of Airflow 2.0 we agreed to certain rules we follow for Python and Kubernetes support. They are based on the official release schedule of Python and Kubernetes, nicely summarized in the [Python Developer’s Guide](https://devguide.python.org/#status-of-python-branches) and [Kubernetes version skew policy](https://kubernetes.io/releases/version-skew-policy/)._ 

## Additional Resources

For more details, please refer:

1. [Apache Airflow documentation](https://airflow.apache.org/docs/apache-airflow/stable/installation/supported-versions.html#support-for-python-and-kubernetes-versions)
2. [Apache Airflow Requirements](https://github.com/apache/airflow#requirements)