# Fluent

### Fluentd (aggregator)
* [Official Docs](https://docs.fluentd.org)
* [Github : Bitnami](https://github.com/bitnami/charts/tree/master/bitnami/fluentd/)

##### custom value : fluentd.yaml
* forwarder 사용하지 않으므로 `enabled: false`
* aggregator replicas 수정
* output으로 elasticsearch를 사용하기 위해, envVar 설정
```bash
$ k get secret {{ elasticsearch CRD .metadata.name }}-es-elastic-user -n elastic \
    -o go-template='{{.data.elastic | base64decode}}'
```
* configmap 수정( Input -> Filter -> Output )

<br>

### Fluentbit (Log collector)
* [Docs](https://docs.fluentbit.io/manual/v/1.3/)
* [Github](https://github.com/fluent/helm-charts/tree/main/charts/fluent-bit)

##### custom value : fluentbit.yaml
* log aggregator를 fluentd로 사용하므로, fluentd svc를 env로 설정
* flush interval 설정
* config 설정