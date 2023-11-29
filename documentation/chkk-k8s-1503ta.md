---
title: An infinite loop during exemplar parsing causes Prometheus to crash in certain configurations
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

We recommend upgrading your Prometheus version to `v2.47.0` or greater. 

## How to fix it, short-term workaround? (Mitigation)

Avoid the use of the following configurations in Prometheus:

- `--enable-feature=native-histograms`

This feature flag is provided as an argument to the Prometheus deployment resource

```yaml YAML
apiVersion: apps/v1
kind: Deployment
metadata:
spec:
  template:
    spec:
      containers:
      - args:
        - --enable-feature=native-histograms
```

- `scrape_classic_histograms`

This configuration is specified under the `scrape_config` [section](https://prometheus.io/docs/prometheus/latest/configuration/configuration/#scrape_config) of the prometheus config ([example](https://github.com/prometheus/prometheus/blob/b6f903b5f92b5458ad2244d9f442f7f859c01eb3/documentation/examples/prometheus.yml#L21)). It  needs to be set to `True` (it is `False` by default) and requires `native-histogram` to be enabled.

```yaml
global:
  scrape_interval: 15s # Set the scrape interval to every 15 seconds. Default is every 1 minute.
  evaluation_interval: 15s # Evaluate rules every 15 seconds. The default is every 1 minute.
  # scrape_timeout is set to the global default (10s).

# Alertmanager configuration
alerting:
  alertmanagers:
    - static_configs:
        - targets:
          # - alertmanager:9093

# Load rules once and periodically evaluate them according to the global 'evaluation_interval'.
rule_files:
  # - "first_rules.yml"

scrape_configs:
  - job_name: "prometheus"
  	
    # Enabling parallel scraping of classic histograms
    scrape_classic_histograms: true
    
    static_configs:
      - targets: ["localhost:9090"]
      
```

- `--enable-feature=exemplar-storage`

This feature flag is provided as an argument to the Prometheus deployment resource

```yaml YAML
apiVersion: apps/v1
kind: Deployment
metadata:
spec:
  template:
    spec:
      containers:
      - args:
        - --enable-feature=exemplar-storage
```

## What is the impact? (Availability Impact)

Using any of the configurations, mentioned above, whether individually or in combination, has the potential to cause Prometheus to crash. This, in turn, would stop the collection of important metrics and alerts, impacting the cluster by hampering the ability to monitor its overall health, potentially resulting in unplanned service disruptions.

## Why does this exist? (Root Cause)

This defect was introduced in PR [#12557](https://github.com/prometheus/prometheus/pull/12557)  in the `prometheus/prometheus` Github repository. This PR introduced multiple exemplar parsing within native histograms aimed to repeatedly invoke the **`Exemplar`** method of the parser until it ceased to yield valid results. However, the `protobuf` parser code wasn't correctly updated for the old case of a single exemplar for a classic bucket (if actually parsed as a classic bucket) and a single exemplar on a counter. In those cases, the method would return `true` forever, yielding the same exemplar again and again, and leading to an endless loop.

## Who is impacted and when? (Trigger Conditions)

Prometheus `v2.46.0` will have this risk.

## Additional Resources

For more information, please refer to 

1. [Github Issue](https://github.com/prometheus/prometheus/issues/12731)
2. [PR that fixed this issue](https://github.com/prometheus/prometheus/pull/12737)