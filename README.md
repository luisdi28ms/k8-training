# Minikube Step by Step


Start minikube:

```bash
minikube start --extra-config "apiserver.cors-allowed-origins=["http://boot.dev"]"
```

Launch dashboard on separate shell:

```bash
minikube dashboard --port=63840
```

Create a deployment:

```bash
kubectl create deployment synergychat-web --image=docker.io/bootdotdev/synergychat-web:latest
```

Open port for the deployment (get pod name first):

```bash
kubectl get pods -o wide
kubectl port-forward PODNAME 8080:8080
```

You can edit the deployment resources with:

```bash
kubectl edit deployment synergychat-web
```

You can see the logs of a pod and delete them:

```bash
kubectl logs PODNAME
kubectl delete pod PODNAME
```

Start a proxy server on my machine:

```bash
kubectl proxy
```

Inspect Deployment's YAML file:

```bash
kubectl get deployment synergychat-web -o yaml
kubectl describe pod PODNAME
```

Apply changes in deployment or configmap file with:

```bash
kubectl apply -f FILENAME
```

Enable ingress in minikube:

```bash
minikube addons enable ingress
```

Enable metrics in minikube:

```bash
minikube addons enable metrics-server
```

Forward ingress to localmachine:

```bash
minikube tunnel -c
```

# Namespaces

Get namespaces:

```bash
kubectl get ns
```

Create namespaces:

```bash
kubectl create ns NS_name
```




Note: If something goes wrong can always delete minikube and start from scratch:

```bash
minikube stop
minikube delete
```