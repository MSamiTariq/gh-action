---
title: Your current version of Redis Enterprise has reached end-of-life.
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

We strongly recommend to upgrade Redis Enterprise to a supported version which is `v6.2`.

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

The version of Redis Enterprise you are running has reached end-of-life, which means you cannot receive security updates, technical support and the software may have incompatibilities leading to unknown behavior.

## Why does this exist? (Root Cause)

As per official documentation of Redis  
_End-of-Life for a given Major release occurs 18 months after the formal release of that version._

Given below is their release schedule.

| Version | Release Date   | End of Life (EOL) |
| :------ | :------------- | :---------------- |
| `v7.2`  | August, 2023 | TBD               |
| `v6.4`  | February, 2023 | February 28, 2025               |
| `v6.2`  | August, 2021   | August 31, 2024   |
| `v6.0`  | May, 2020      | May 31, 2022      |
| `v5.6`  | April, 2020    | October 31, 2021  |
| `v5.4`  | December, 2018 | December 31, 2020 |
| `v5.2`  | June, 2018     | December 31, 2019 |

## Additional Resources

For more details, please refer to the [official Redis documentation ](https://docs.redis.com/latest/rs/installing-upgrading/product-lifecycle/#endoflife-schedule)