# setting up traefik

Guide : `https://docs.traefik.io/user-guide/kubernetes/`

## Slim version

exec in terminal

```bash
# create rbac, ds and ui
kubectl apply -f https://raw.githubusercontent.com/containous/traefik/master/examples/k8s/traefik-rbac.yaml
kubectl apply -f https://raw.githubusercontent.com/containous/traefik/master/examples/k8s/traefik-ds.yaml
kubectl apply -f https://raw.githubusercontent.com/containous/traefik/master/examples/k8s/ui.yaml
# update your machine Host Database and
# route traefik-ui.minikube to minikube host.
echo "$(minikube ip) traefik-ui.minikube" | sudo tee -a /etc/hosts
# curl -v traefik-ui.minikube
# * Rebuilt URL to: traefik-ui.minikube/
# *   Trying 192.168.99.100...
# * TCP_NODELAY set
# * Connected to traefik-ui.minikube (192.168.99.100) port 80 (#0)
# > GET / HTTP/1.1
# > Host: traefik-ui.minikube
# > User-Agent: curl/7.54.0
# > Accept: */*
# >
# < HTTP/1.1 302 Found
# < Content-Length: 34
# < Content-Type: text/html; charset=utf-8
# < Date: Fri, 20 Jul 2018 08:32:34 GMT
# < Location: /dashboard/
# <
# <a href="/dashboard/">Found</a>.

# * Connection #0 to host traefik-ui.minikube left intact
```
