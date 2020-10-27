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
