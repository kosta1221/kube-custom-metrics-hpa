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
