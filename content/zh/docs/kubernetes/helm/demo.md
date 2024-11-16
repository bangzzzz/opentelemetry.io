---
title: OpenTelemetry Demo Chart
linkTitle: Demo Chart
---

OpenTelemetry 的示例程序(/docs/demo/) 是一个使用微服务的分布式系统,  这是一个基于微型服务的分布式系统，用于演示 OpenTelemetry 在接近真实生产环境中的场景实现。

为此，OpenTelemetry 社区构建了 [OpenTelemetry Demo Helm Chart](https://github.com/open-telemetry/opentelemetry-helm-charts/tree/main/charts/opentelemetry-demo)，以方便在 Kubernetes 中简化安装 OpenTelemetry Demo 。


## Configuration

The Demo helm chart's default `values.yaml` is ready to be installed. All
components have had their memory limits tuned to optimize performance, which may
cause issues if your cluster is not large enough. The entire installation is
restricted to ~4 Gigabytes of memory, but may use less.

All the configuration options (with comments) available in the chart can be
viewed in its
[`values.yaml` file](https://github.com/open-telemetry/opentelemetry-helm-charts/blob/main/charts/opentelemetry-demo/values.yaml),
and detailed descriptions can be found in the
[chart's README](https://github.com/open-telemetry/opentelemetry-helm-charts/tree/main/charts/opentelemetry-demo#chart-parameters).

## Installation

To install the chart with the release name `my-otel-demo`, run the following
command:

```sh
helm install my-otel-demo open-telemetry/opentelemetry-demo
```

Once installed, all services are made available via the Frontend proxy
(<http://localhost:8080>) by running these commands:

```sh
kubectl port-forward svc/my-otel-demo-frontendproxy 8080:8080
```

Once the proxy is exposed, you can also visit the following paths

| Component         | Path                              |
| ----------------- | --------------------------------- |
| Web store         | <http://localhost:8080>           |
| Grafana           | <http://localhost:8080/grafana>   |
| Feature Flags UI  | <http://localhost:8080/feature>   |
| Load Generator UI | <http://localhost:8080/loadgen>   |
| Jaeger UI         | <http://localhost:8080/jaeger/ui> |

In order for spans from the Web store to be collected you must expose the
OpenTelemetry Collector OTLP/HTTP receiver:

```sh
kubectl port-forward svc/my-otel-demo-otelcol 4318:4318
```

For more details on using the demo in Kubernetes, see
[Kubernetes deployment](/docs/demo/kubernetes-deployment/).
