---
title: Prometheus fails to recover from a corrupted or bad chunk of data leading to a crash
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Upgrade your prometheus version to `v2.39.0` or greater.

## How to fix it, short-term workaround? (Mitigation)

A potential workaround to recover from the "invalid magic number 0" crash in Prometheus is deleting the chunk file mentioned in the Pod logs by identifying the PV used. However, this approach is not recommended as it may result in data loss.  
Regardless, detailed steps to do so can be found [here](https://support.d2iq.com/hc/en-us/articles/4409472647060-Prometheus-Pods-Fail-to-Start-Due-to-Empty-Chunk-File#:~:text=The%20solution%20is%20to%20identify%20the%20PV%20that%20Prometheus%20Server%20is%20using%2C%20and%20then%20delete%20the%20chunk%20file%20mentioned%20in%20the%20Prometheus%20Pod%20logs.%20This%20issue%20can%20affect%20any%20Prometheus%20deployment%20but%20for%20our%20example%20resolution%20we%20are%20using%20the%20default%20Prometheus%20Addon%20that%20ships%20with%20Konvoy%201.6.0.)

## What is the impact? (Availability Impact)

Prometheus crashing can result in the loss of monitoring data and the inability to generate metrics and alerts. This can lead to delayed or missed detection of critical issues, impairing the ability to respond promptly and compromising the overall availability and reliability of the monitored systems.

## Why does this exist? (Root Cause)

The presence of a defect in Prometheus causes it to crash with an "invalid magic number 0" error whenever it encounters a corrupt file. While a check was implemented to handle empty files, it was overlooked for files filled with zeroes. As a consequence, instead of being able to gracefully recover, the entire Prometheus deployment crashes when confronted with such files.

## Who is impacted and when? (Trigger Conditions)

_Affected Versions_  
All clusters using Prometheus versions `v2.18`to`v2.38` contain this Latent Availability Risk.

## Additional Resources

For more details, please refer to the following:

- [GitHub Issue](https://github.com/prometheus/prometheus/issues/10679)
- [GitHub Issue](https://github.com/prometheus/prometheus/issues/7397)
- [GitHub PR](https://github.com/prometheus/prometheus/pull/11338)