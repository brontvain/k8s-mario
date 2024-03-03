##CREATE CLUSTER
kind create cluster --config kind-config.yaml --name mario

##SETUP METALLB
kubectl apply -f https://raw.githubusercontent.com/metallb/metallb/v0.14.3/config/manifests/metallb-native.yaml
kubectl get pods -n metallb-system
kubectl apply -f metallb-mario.yaml -n metallb-system

##Install Mario
kubectl apply -f supermario-k8s/deployment.yaml
kubectl apply -f supermario-k8s/service.yaml