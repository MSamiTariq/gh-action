---
title: Use new filter names for EnvoyFilter
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Use the new filter names for EnvoyFilter as specified below:

| Canonical Names                               | Deprecated Names                  |
| --------------------------------------------- | --------------------------------- |
| envoy.access_loggers.file                     | envoy.file_access_log             |
| envoy.access_loggers.http_grpc                | envoy.http_grpc_access_log        |
| envoy.access_loggers.tcp_grpc                 | envoy.tcp_grpc_access_log         |
| envoy.filters.http.buffer                     | envoy.buffer                      |
| envoy.filters.http.cors                       | envoy.cors                        |
| envoy.filters.http.csrf                       | envoy.csrf                        |
| envoy.filters.http.dynamo                     | envoy.http_dynamo_filter          |
| envoy.filters.http.ext_authz                  | envoy.ext_authz                   |
| envoy.filters.http.fault                      | envoy.fault                       |
| envoy.filters.http.grpc_http1_bridge          | envoy.grpc_http1_bridge           |
| envoy.filters.http.grpc_json_transcoder       | envoy.grpc_json_transcoder        |
| envoy.filters.http.grpc_web                   | envoy.grpc_web                    |
| envoy.filters.http.gzip                       | envoy.gzip                        |
| envoy.filters.http.health_check               | envoy.health_check                |
| envoy.filters.http.ip_tagging                 | envoy.ip_tagging                  |
| envoy.filters.http.lua                        | envoy.lua                         |
| envoy.filters.http.ratelimit                  | envoy.rate_limit                  |
| envoy.filters.http.router                     | envoy.router                      |
| envoy.filters.http.squash                     | envoy.squash                      |
| envoy.filters.listener.http_inspector         | envoy.listener.http_inspector     |
| envoy.filters.listener.original_dst           | envoy.listener.original_dst       |
| envoy.filters.listener.original_src           | envoy.listener.original_src       |
| envoy.filters.listener.proxy_protocol         | envoy.listener.proxy_protocol     |
| envoy.filters.listener.tls_inspector          | envoy.listener.tls_inspector      |
| envoy.filters.network.client_ssl_auth         | envoy.client_ssl_auth             |
| envoy.filters.network.echo                    | envoy.echo                        |
| envoy.filters.network.ext_authz               | envoy.ext_authz                   |
| envoy.filters.network.http_connection_manager | envoy.http_connection_manager     |
| envoy.filters.network.mongo_proxy             | envoy.filters.network.mongo_proxy |
| envoy.filters.network.ratelimit               | envoy.ratelimit                   |
| envoy.filters.network.redis_proxy             | envoy.redis_proxy                 |
| envoy.filters.network.tcp_proxy               | envoy.tcp_proxy                   |
| envoy.stat_sinks.dog_statsd                   | envoy.dog_statsd                  |
| envoy.stat_sinks.metrics_service              | envoy.metrics_service             |
| envoy.stat_sinks.statsd                       | envoy.statsd                      |
| envoy.tracers.dynamic_ot                      | envoy.dynamic.ot                  |
| envoy.tracers.lightstep                       | envoy.lightstep                   |
| envoy.tracers.zipkin                          | envoy.zipkin                      |

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## Why does this exist? (Root Cause)

In Istio version `v1.9` and later, EnvoyFilter will only use new filter names. Filters using deprecated names will no longer be applied.

## Additional Resources

For more details on the supported filter names for Envoy, please refer to the [official Envoy documentation]  
(<https://www.envoyproxy.io/docs/envoy/latest/version_history/v1.14.0#deprecated>)