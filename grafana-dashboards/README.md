# Grafana dasboard

## build the configmap

```bash
kubectl create configmap grafana-dashboard-argocd  --from-file=argocd.json --dry-run=client --output yaml > configmap-grafana-dashboard-argocd.yaml
```

```yaml
  namespace: monitoring
  labels:
    grafana_dashboard: "1"
```