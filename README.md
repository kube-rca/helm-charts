# helm-charts

```shell
# Argo CD Install Command
helm upgrade --install -n argocd argocd charts/argo-cd -f charts/argo-cd/kube-rca-values.yaml

# Argo CD Applications Install Command
helm upgrade --install -n argocd argo-applications charts/argo-applications -f charts/argo-applications/kube-rca-values.yaml

# kube-prometheus-stack Install Command
helm upgrade --install -n monitoring kube-prometheus-stack charts/kube-prometheus-stack -f charts/kube-prometheus-stack/kube-rca-values.yaml
```
