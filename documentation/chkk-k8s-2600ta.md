---
title: Your current version of Envoy has reached End-of-Life
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Upgrade your version of Envoy to the latest supported version.

|   Version  | Release Date | End of Life |
| :--------: | :----------: | :---------: |
|   `v1.12`  |  2019/10/31  |  2020/10/31 |
|   `v1.13`  |  2020/01/20  |  2021/01/20 |
|   `v1.14`  |  2020/04/08  |  2021/04/08 |
|   `v1.15`  |  2020/07/07  |  2021/07/07 |
|   `v1.16`  |  2020/10/08  |  2021/10/08 |
|   `v1.17`  |  2021/01/11  |  2022/01/11 |
|   `v1.18`  |  2021/04/15  |  2022/04/15 |
|   `v1.19`  |  2021/07/13  |  2022/07/13 |
|   `v1.20`  |  2021/10/05  |  2022/10/05 |
|   `v1.21`  |  2022/01/12  |  2023/01/12 |
|   `v1.22`  |  2022/04/15  |  2023/04/15 |
|   `v1.23`  |  2022/07/15  |  2023/07/15 |
|   `v1.24`  |  2022/10/19  |  2023/10/19 |
|   `v1.25`  |  2023/01/18  |  2024/01/18 |
|   `v1.26`  |  2023/04/18  |  2024/04/18 |
|   `v1.27`  |  2023/07/27  |  2024/07/27 |
| `v1.28` |  2023/10/19  |  2024/10/19 |

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

If a version of Envoy reaches end-of-life, it is no longer supported. This may result in the software having incompatibilities leading to unknown behavior.

## Why does this exist? (Root Cause)

As per Envoy’s official documentation, in order to accommodate downstream projects, new Envoy releases are produced on a fixed release schedule (the 15th day of each quarter), with an acceptable delay of up to 2 weeks, with a hard deadline of 3 weeks.

## Additional Resources

For more details, please refer to the [official Envoy documentation](https://github.com/envoyproxy/envoy/blob/main/RELEASES.md#major-release-schedule).