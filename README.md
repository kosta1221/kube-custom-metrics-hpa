# kube-custom-metrics-hpa

HPA based on custom metrics in kubernetes (rabbitmq example)

# Pre Requisites

1. Kind/ minikube local kubernetes cluster and kubectl configured for that cluster.
2. Familiarity with HPA concepts in kubernetes.
3. Helm

# Setup

1. Deploy Prometheus Operator. We will use [kube-prometheus](https://prometheus-operator.dev/docs/prologue/quick-start/) for an easy quick start.

2. Deploy Prometheus-Adapter for custom metrics (v1beta1.custom.metrics.k8s.io api) through helm, using the `values.yaml` from this repo.

3. Deploy rabbitmq cluster operator, and then the [hello world example](https://www.rabbitmq.com/kubernetes/operator/quickstart-operator.html) RabbitmqCluster custom resource with the yaml from this repo (for the rabbitmq_prometheus plugin).

4. Monitoring RabbitMq with Prometheus ->

Cluster Operator deploys RabbitMQ clusters with the rabbitmq_prometheus plugin enabled. The plugin exposes a Prometheus-compatible metrics endpoint.

The Prometheus Operator defines the custom resource definitions (CRDs) ServiceMonitor, PodMonitor, and PrometheusRule. ServiceMonitor and PodMonitor CRDs allow to declaratively define how a dynamic set of services and pods should be monitored.

To monitor all RabbitMQ clusters, run:

```bash
kubectl apply --filename https://raw.githubusercontent.com/rabbitmq/cluster-operator/main/observability/prometheus/monitors/rabbitmq-servicemonitor.yml
```

To monitor RabbitMQ Cluster Operator, run:

```bash
kubectl apply --filename https://raw.githubusercontent.com/rabbitmq/cluster-operator/main/observability/prometheus/monitors/rabbitmq-cluster-operator-podmonitor.yml
```

5. Configure Permissions for the Prometheus Operator

```bash
kubectl apply -f prometheus-roles.yaml
```
