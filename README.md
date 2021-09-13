# istio
Learn Istio service mesh by simple examples.
It covers:
- Traffic shifting mechanisms like - Weighted routing, canary, dark launch via mirroring, http headers etc.
- Adding custom filter to istio-proxy
- Traffic visualisation via Kiali
- In future will cover security aspects

In future it will also cover Security and  etc, 

## Step 1
Create a kubernetes cluster on your favourite cloud platform

## Step 2
Install Istio following -> https://istio.io/latest/docs/setup/getting-started/

## Step 3
Clone this repo

## Step 4
Apply the configuration using 
Please note, you need to first apply all files except those ending with -vs.
Once you have those applied then try applying -vs files one at a time to see the effect.
```
kubectl apply -f <name of yaml file>
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
<img width="2142" alt="Screenshot 2021-09-13 at 7 38 23 PM" src="https://user-images.githubusercontent.com/17019260/133098776-cfc95ee3-e1fd-4fca-b90f-925e5dd7df71.png">
