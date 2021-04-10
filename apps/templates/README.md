

kubectl get secret jenkins-operator-credentials-jenkins -n jenkins-operator -o 'jsonpath={.data.user}' | base64 -d && echo
kubectl get secret jenkins-operator-credentials-jenkins -n jenkins-operator -o 'jsonpath={.data.password}' | base64 -d && echo
