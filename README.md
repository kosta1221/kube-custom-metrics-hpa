# kube-custom-metrics-hpa

HPA based on custom metrics in kubernetes (rabbitmq example)

# Pre Requisites

1. Kind/ minikube local kubernetes cluster and kubectl configured for that cluster.
2. Familiarity with HPA concepts in kubernetes.
3. Helm

# Setup

1. Deploy Prometheus Operator. We will use [kube-prometheus](https://prometheus-operator.dev/docs/prologue/quick-start/) for an easy quick start.
