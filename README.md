# helm-charts

```shell
# Argo CD Install Command
helm upgrade --install -n argocd argocd charts/argo-cd -f charts/argo-cd/kube-rca-values.yaml

# Argo CD Applications Install Command
helm upgrade --install -n argocd argo-applications charts/argo-applications -f charts/argo-applications/kube-rca-values.yaml
```
