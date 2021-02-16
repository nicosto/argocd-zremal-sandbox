

## Jenkins operator

retreive username and password

https://jenkinsci.github.io/kubernetes-operator/docs/getting-started/latest/deploy-jenkins/


```bash
kubectl -n jenkins-operator get secret jenkins-operator-credentials-jenkins -o 'jsonpath={.data.user}' | base64 -d ; echo
kubectl -n jenkins-operator get secret jenkins-operator-credentials-jenkins -o 'jsonpath={.data.password}' | base64 -d ; echo
```