# Learning KUDO

See: https://kudo.dev/

## Minikube

```sh
minikube start --cpus=4 --memory=4096 --disk-size=20g --kubernetes-version=1.18.3
```

The latest version of K8s has deprecated features, so when working with KUDO there are a lot of warnings.

## Install KUDO

```sh
kubectl krew install kudo
kubectl kudo init --unsafe-self-signed-webhook-ca -w  #self signed CA, without cert-manager
```

### First operator

Install: `kubectl kudo install ./operator`
status: `k kudo plan status --instance=first-one-instance`
delete: `k kudo uninstall --instance=first-one-instance`
upgrade: `k kudo upgrade ./first_one/operator --instance=first-one-instance`
update: `k kudo update --instance=first-one-instance -p message=How+are+you\?`

## Minikube

* minikube start --memory=4096 --cpus=4 --kubernetes-version=v1.18.3 --disk-size=20g

## Istio

* curl -L https://istio.io/downloadIstio | sh -
* istioctl install --set profile=demo
* kubectl label namespace default istio-injection=enabled

## Install KUDO

* kubectl krew install kudo
* kubectl kudo init --unsafe-self-signed-webhook-ca -w

## Operator

* k kudo install ./first_one/operator
* k kudo uninstall --instance=first-one-instance

## Monitor

target url: http://myserver.local/

* cli watch :  watch 'http myserver.local | awk "/<pre/,/pre>/"'

* traffic: k kudo update --instance=first-one-instance -p traffic=50

* minikube tunnel --cleanup



## Demo

* install: k kudo install ./first_one/operator
* deploy new version: k kudo update --instance=first-one-instance -p version=v2
* update msg version for v2: k kudo update --instance=first-one-instance -p message=V2+how+are+you\?
* start switching traffic: 
    * k kudo update --instance=first-one-instance -p traffic=50
    * k kudo update --instance=first-one-instance -p traffic=0
cleanup:
    * delete old app: kubectl kudo plan trigger --name=cleanup-old --instance=first-one-instance
    * change original:  k kudo update --instance=first-one-instance -p original=v2
    * traffic: k kudo update --instance=first-one-instance -p traffic=100

* uninstall: k kudo uninstall --instance=first-one-instance
