# istio
Learn Istio service mesh by simple examples.
It covers traffic shifting mechanisms like - Weighted routing, canary, dark launch via mirroring, http headers etc.
It also covers traffic visualisation via Kiali. 

In future it will also cover Security and Envoy Filter customization etc, 

## Step 1
Create a kubernetes cluster on your favourite cloud platform

## Step 2
Install Istio following -> https://istio.io/latest/docs/setup/getting-started/

## Step 3
Clone this repo

## Step 4
Apply the configuration using 
```
kubectl apply -f .
```
## Step 5
Use browser or Postman client to send traffic and recieve response

## Step 6
Check visualization on Kiali, Grafana etc.
For example to expose KIALI follow below steps and repeat for Grafana etc. ->
```
kubectl expose service kiali --type=LoadBalancer --name=kiali-svc --namespace istio-system
export KIALI_URL=$(kubectl get svc istio-ingressgateway -n istio-system  -o jsonpath="{.status.loadBalancer.ingress[0]['hostname','ip']}"):$(kubectl get svc kiali-svc -n istio-system -o 'jsonpath={.spec.ports[0].nodePort}')
echo http://${KIALI_URL}
```
