---
title: OpenTelemetry Helm Charts
linkTitle: Helm Charts
---

## 简介

[Helm](https://helm.sh/) Helm 是 Kubernetes 的软件包管理器。

如果你选择使用 Helm，你可以使用 [OpenTelemetry Helm Charts](https://github.com/open-telemetry/opentelemetry-helm-charts) 来管理和安装
[OpenTelemetry Collector](/docs/collector), [OpenTelemetry Operator](/docs/kubernetes/operator), 和[OpenTelemetry Demo](/docs/demo).

使用以下命令添加 OpenTelemetry Helm 软件源：
```sh
helm repo add open-telemetry https://open-telemetry.github.io/opentelemetry-helm-charts
```
