# hello-world

##

```bash
sudo snap alias microk8s.kubectl kubectl
```

### How to add an image to Github packages

Create a new token first and add it to `GH_TOKEN.txt` from [Personal access tokens](https://github.com/settings/tokens)
```bash
#
# Step 1: Authenticate
#
cat ~/GH_TOKEN.txt | docker login docker.pkg.github.com -u nicolasramy --password-stdin`

# WARNING! Your password will be stored unencrypted in /home/nicolas/.docker/config.json.
# Configure a credential helper to remove this warning. See
# https://docs.docker.com/engine/reference/commandline/login/#credentials-store
# 
# Login Succeeded

#
# Step 2: Tag
#
docker tag "$IMAGE_ID" docker.pkg.github.com/nicolasramy/hello-world/"$IMAGE_NAME":"$VERSION"
# or
docker build -t docker.pkg.github.com/nicolasramy/hello-world/"$IMAGE_NAME":"$VERSION" nginx/.

# Sending build context to Docker daemon   5.12kB
# Step 1/4 : FROM nginx:alpine
#  ---> 6f715d38cfe0
# Step 2/4 : MAINTAINER Nicolas Ramy <devops@darkelda.com>
#  ---> Using cache
#  ---> 96a70fe1d558
# Step 3/4 : ADD default.conf /etc/nginx/conf.d/default.conf
#  ---> 82c4c055c230
# Step 4/4 : ADD index.html /var/www/index.html
#  ---> 31567f01026d
# Successfully built 31567f01026d
# Successfully tagged docker.pkg.github.com/nicolasramy/hello-world/nginx:latest

# 
# Step 3: Publish
# 
docker push docker.pkg.github.com/nicolasramy/hello-world/"$IMAGE_NAME":"$VERSION"

# The push refers to repository [docker.pkg.github.com/nicolasramy/hello-world/nginx]
# 49c5b6d1fb03: Pushed 
# f3d351f3c2c1: Pushed 
# 6ad8d562c843: Pushed 
# 425ee8569962: Pushed 
# 5d9ee84be1ec: Pushed 
# 6bcd003260b2: Pushed 
# 50644c29ef5a: Pushed 
# latest: digest: sha256:3616cf3250680da614306130f617b3b823f9e7622c96981846ef5db8f2ee7ca6 size: 1774
```


## Kubernetes

```bash
kubectl -n hello-world create secret generic regcred --from-file=.dockerconfigjson=docker-config.json --type=kubernetes.io/dockerconfigjson
```
