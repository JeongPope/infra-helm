# ECK (Elastic Cloud on Kubernetes)
Operator ECK를 활용하여 elasticsearch, kibana 를 관리한다.  

* [Official](https://www.elastic.co/guide/en/cloud-on-k8s/master/index.html)
* [Operatorhub](https://operatorhub.io/operator/elastic-cloud-eck)
* [Example CRD of Elasticsearch, Kibana](https://github.com/JeongPope/infra-k8s/tree/master/kubernetes/common/devops/eck)

##### Uninstall
```
// Uninstall
$ kubectl delete -n {{ namespace }} \
    serviceaccount/elastic-operator \
    secret/elastic-webhook-server-cert \
    clusterrole.rbac.authorization.k8s.io/elastic-operator \
    clusterrole.rbac.authorization.k8s.io/elastic-operator-view \
    clusterrole.rbac.authorization.k8s.io/elastic-operator-edit \
    clusterrolebinding.rbac.authorization.k8s.io/elastic-operator \
    service/elastic-webhook-server \
    configmap/elastic-operator \ 
    statefulset.apps/elastic-operator \
    validatingwebhookconfiguration.admissionregistration.k8s.io/elastic-webhook.k8s.elastic.co
```
<br>