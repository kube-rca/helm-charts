# helm-charts

```shell
# Argo CD Install Command
helm upgrade --install -n argocd argocd -f kuberca-values.yaml .

# Argo CD Applications Install Command
helm upgrade --install -n argocd argo-applications -f kuberca-values.yaml .
```