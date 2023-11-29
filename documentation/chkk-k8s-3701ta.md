---
title: Unsupported version of Apache Airflow
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

We strongly recommend using an Apache Airflow version that has not reached End of Life yet.

| Version | Current Patch/Minor | State     | First Release | Limited Support | EOL/Terminated |
| :------ | :------------------ | :-------- | :------------ | :-------------- | :------------- |
| `v2`    | `v2.7.2`            | Supported | Dec 17, 2020  | TBD             | TBD            |
| `v1.10` | `v1.10.15`          | EOL       | Aug 27, 2018  | Dec 17, 2020    | June 17, 2021  |
| `v1.9`  | `v1.9.0`            | EOL       | Jan 03, 2018  | Aug 27, 2018    | Aug 27, 2018   |
| `v1.8`  | `v1.8.2`            | EOL       | Mar 19, 2017  | Jan 03, 2018    | Jan 03, 2018   |
| `v1.7`  | `v1.7.1.2`          | EOL       | Mar 28, 2016  | Mar 19, 2017    | Mar 19, 2017   |

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Running an unsupported version of Apache Airflow will lead to unintended behavior and functionality may not work as expected. 

## Why does this exist? (Root Cause)

As per Apache Airflow official documentation, 

_Limited support versions will be supported with security and critical bug fix only. EOL versions will not get any fixes nor support. We highly recommend installing the latest Airflow release which has richer features._ 

## Additional Resources

For more details, please refer to the official [Apache Airflow documentation](https://airflow.apache.org/docs/apache-airflow/stable/installation/supported-versions.html#version-life-cycle)