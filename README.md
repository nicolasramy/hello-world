# hello-world

## Before you start

Make sure you have install MicroK8s on your computer and have clone this repository.
If you need [more information on the installation](https://microk8s.io/docs).

```bash
sudo snap install microk8s --classic
```

To go faster with `kubectl` command, you can create and alias to avoid repeat 
the `microk8s.` prefix everytime.

```bash
sudo snap alias microk8s.kubectl kubectl
```

----

Docker Compose is only used to make sure the image we will build and used work properly.

## MicroK8s add-ons required

Add-ons to enabled for this tutorial

- dashboard
- dns
- registry

```bash
microk8s enable dashboard dns registry
```

### Dashboard

The dashboard is a great tool to have access to the cluster visualization and
the definition of resources used and available on your Kubernetes cluster.

### DNS

### Registry

The registry is a simple Docker Registry, with no authentication by default
and 

## How to add an image to your local registry?

### Build with tag

```bash
docker build -t localhost:32000/hello-world/nginx:latest nginx/
docker build -t localhost:32000/hello-world/rust:latest rust/
```

### Push to your local registry

```bash
docker push localhost:32000/hello-world/nginx:latest
docker push localhost:32000/hello-world/rust:latest
```


## Kubernetes

```bash
cd kubernetes/
kubectl apply -f namespace.yml

kubectl apply -f hello-world/
```

To access to the application, you have 3 solutions:
- port forward
- proxy
- ingress
