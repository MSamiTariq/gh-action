---
title: Unsupported Version of PostgreSQL
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Upgrade to one of the supported PostgreSQL versions, preferably to the latest minor release of that version. The following table depicts currently supported versions

| Version | Current Minor |    First Release   |   Final Release   |
| :-----: | :-----------: | :----------------: | :---------------: |
|  `v16`  |    `v16.0`    | September 14, 2023 |  November 9, 2028 |
|  `v15`  |    `v15.3`    |  October 13, 2022  | November 11, 2027 |
|  `v14`  |    `v14.8`    | September 30, 2021 | November 12, 2026 |
|  `v13`  |    `v13.11`   | September 24, 2020 | November 13, 2025 |
|  `v12`  |    `v12.15`   |   October 3, 2019  | November 14, 2024 |
|  `v11`  |    `v11.20`   |  October 18, 2018  |  November 9, 2023 |

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Running an unsupported version of PostgreSQL will lead to unintended behavior and functionality may not work as expected.

## Why does this exist? (Root Cause)

PostgreSQL recommends using one of the officially supported major versions of PostgreSQL. Furthermore, it is suggested to stay on the latest minor release of whichever major version is being used.

## Additional Resources

For more information see: [PostgreSQL Versioning Policy](https://www.postgresql.org/support/versioning/)