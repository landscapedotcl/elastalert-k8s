# elastalert-k8s

Elastalert configuration for Kubernetes and Elastic Cloud

Note: Docker image is based in https://github.com/jertel/elastalert-docker

## Docker ( local test )

* `docker build -t elastalert:0.2.4 .`

* ``docker run --rm -v `pwd`/elastalert_config.yaml:/opt/config/elastalert_config.yaml -v `pwd`/rules:/opt/elastalert/alert_rules  elastalert:0.2.4``

## Kubernetes

Creates configmap with rules:

* `kubectl create configmap elastalert-rules --from-file=rules/ --namespace=kube-system -o yaml`

Creates configmap with elastalert config:

* `kubectl create configmap elastalert-config --from-file=elastalert_config.yaml --namespace=kube-system -o yaml`

Deploy

* `kubectl apply -f elastalert-deployment.yaml -n kube-system`
