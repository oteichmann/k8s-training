# Ingress installation

### Install nginx
kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/master/deploy/static/provider/baremetal/deploy.yaml

### Patch node port
kubectl -n ingress-nginx patch svc ingress-nginx-controller --type merge -p '{"spec":{"ports": [{"port": 80,"name":"http","nodePort":31080}]}}'