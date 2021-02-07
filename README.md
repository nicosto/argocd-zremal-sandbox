# install


## do it

```
helm repo add argo-cd https://argoproj.github.io/argo-helm
```

```
helm dep update charts/argo-cd/
```

```
helm install --namespace=argocd --create-namespace argocd ./bootstrap
```

```
kubectl -n argocd port-forward svc/argo-cd-argocd-server 9080:443
```

```
kubectl -n argocd get pods -l app.kubernetes.io/name=argocd-server -o name | cut -d'/' -f 2
```
## install auto-update 

```
git add apps
git ci -m 'add root app'
git push

helm template ./argocd | kubectl apply -f -
```

## references

https://medium.com/@fache.loic/k3s-traefik-2-9b4646393a1c

https://www.arthurkoziel.com/setting-up-argocd-with-helm/

https://rtfm.co.ua/en/argocd-a-helm-chart-deployment-and-working-with-helm-secrets-via-aws-kms/#ArgCD_a_Helm_chart_deployment
