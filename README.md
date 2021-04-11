# install


## do it

```
helm repo add argo-cd https://argoproj.github.io/argo-helm
```

```
helm dep update ./bootstrap
```

```
helm install --namespace=argocd --create-namespace argocd ./bootstrap 
```

```
kubectl -n argocd port-forward svc/argo-cd-argocd-server 9080:443
```

Get admin password

```
kubectl -n argocd get pods -l app.kubernetes.io/name=argocd-server -o name | cut -d'/' -f 2
```
## install inital jobs
This will install the root job and the Argo CD self update job


```
git add apps
git ci -m 'add root app'
git push

helm template ./jobs-bootstrap | kubectl apply -f -
```

## references

https://medium.com/@fache.loic/k3s-traefik-2-9b4646393a1c

https://www.arthurkoziel.com/setting-up-argocd-with-helm/

https://rtfm.co.ua/en/argocd-a-helm-chart-deployment-and-working-with-helm-secrets-via-aws-kms/#ArgCD_a_Helm_chart_deployment

https://medium.com/@ricardoupiicsa02/how-to-connect-jenkins-for-scm-with-bitbucket-github-gitlab-azure-repos-e115f1ca897f


https://medium.com/hootsuite-engineering/building-docker-images-inside-kubernetes-42c6af855f25
https://kurtmadel.com/posts/native-kubernetes-continuous-delivery/building-container-images-with-kubernetes/
https://github.com/external-secrets/kubernetes-external-secrets
https://yetiops.net/posts/argocd-jenkins-pipeline/
https://github.com/jenkinsci/configuration-as-code-plugin


## Dependency-track

helmchart: https://github.com/evryfs/helm-charts/tree/master/charts/dependency-track
