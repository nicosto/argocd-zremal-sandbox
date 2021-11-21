# install


## do it

```
helm repo add argo-cd https://argoproj.github.io/argo-helm
```

Updatte the boostrap job, this will install argo-cd in the cluster without any jobs.

Agro-cd version is diven by the helm Chart.yaml as a dependency

Let's download the requested chart

```
helm dep update ./bootstrap
```

Now we can deploy argo-cd

```
helm install --namespace=argocd --create-namespace argocd ./bootstrap 
```


Get admin password

```
$ kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d && echo
```

port forward for access

```
kubectl -n argocd port-forward svc/argo-cd-argocd-server 9080:443
```


## install inital jobs
This will install the root job and the Argo CD self update job

```
helm template ./jobs-bootstrap | kubectl apply -f -
```

external repositories:

* apps: https://github.com/nicosto/argocd_apps
* argocd update: https://github.com/nicosto/argocd_argocd


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
