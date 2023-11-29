---
title: Your version of Confluent packaged Apache Kafka is no longer supported
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

We strongly recommend upgrading Confluent packaged Apache Kafka to a supported version.

| Confluent Platform | Release Date       | Standard End of Support |
| :----------------- | :----------------- | :---------------------- |
| `v7.5.x`           | August 25, 2023    | August 25, 2025         |
| `v7.4.x`           | May 3, 2023        | May 3, 2025             |
| `v7.3.x`           | November 4, 2022   | November 4, 2024        |
| `v7.2.x`           | July 6, 2022       | July 6, 2024            |
| `v7.1.x`           | April 5, 2022      | April 5, 2024           |
| `v7.0.x`           | October 27, 2021   | October 27, 2023        |
| `v6.2.x`           | June 8, 2021       | June 8, 2023            |
| `v6.1.x`           | February 9, 2021   | February 9, 2023        |
| `v6.0.x`           | September 24, 2020 | September 24, 2022      |
| `v5.5.x`           | April 24, 2020     | April 24, 2022          |
| `v5.4.x`           | January 10, 2020   | January 10, 2022        |
| `v5.3.x`           | July 19, 2019      | July 19, 2021           |
| `v5.2.x`           | March 28, 2019     | March 28, 2021          |
| `v5.1.x`           | December 14, 2018  | December 14, 2020       |
| `v5.0.x`           | July 31, 2018      | July 31, 2020           |
| `v4.1.x`           | April 16, 2018     | April 16, 2020          |
| `v4.0.x`           | November 28, 2017  | November 28, 2019       |
| `v3.3.x`           | August 1, 2017     | August 1, 2019          |
| `v3.2.x`           | March 2, 2017      | March 2, 2019           |
| `v3.1.x`           | November 15, 2016  | November 15, 2018       |
| `v3.0.x`           | May 24, 2016       | May 24, 2018            |
| `v2.0.x`           | December 7, 2015   | December 7, 2017        |
| `v1.0.0`           | February 25, 2015  | February 25, 2017       |

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Running a Confluent packaged Apache Kafka version that has reached End of Support can lead to unintended behavior and functionality may not work as expected.

## Why does this exist? (Root Cause)

Confluent follows a 2 year Standard Support plan whereas users with a Platinum Support agreement get an additional year of support. Confluent recommends running a supported version of Apache Kafka to continue receiving security updates and technical support.

## Additional Resources

For more details, please refer to the official [Confluent documentation](https://docs.confluent.io/platform/current/installation/versions-interoperability.html#cp-and-apache-ak-compatibility)