# kubernetes-devops-security

## Fork and Clone this Repo

## Jenkins Installation

if found error then run this

`sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys [KEY_ID]`

## Clone to Desktop and VM

## NodeJS Microservice - Docker Image -

`docker run -p 8787:5000 siddharth67/node-service:v1`

`curl localhost:8787/plusone/99`

## NodeJS Microservice - Kubernetes Deployment -

`kubectl create deploy node-app --image siddharth67/node-service:v1`

`kubectl expose deploy node-app --name node-service --port 5000 --type ClusterIP`

`curl node-service-ip:5000/plusone/99`

## Install SonarQube

`docker run -d --name sonarqube -e SONAR_ES_CHECKS_DISABLE=true -p 9000:9000 sonarqube:latest`

## Talisman Installation

`curl https://thoughtworks.github.io/talisman/install.sh > ~/install-talisman.sh`
`chmod +x ~/install-talisman.sh`
`cd your-git-project`
`~/install-talisman.sh`

## Trivy Scan Image

`docker run --rm -v /:/root/.cache/ aquasec/trivy:0.17.2 -q image --exit-code 1 --light openjdk`

### OPA

command for check docker permission
`kubectl exec -it devsecops-686c546c84-9jfwp -- id`

## K8S

Check rollout status
`kubectl rollout history deploy devsecops`

Rollout status
`kubectl rollout status deploy devsecops`

Undo status
`kubectl rollout undo deploy devsecops`

Check Readonly Pod
`kubectl get po [POD_NAME] -o yaml | grep -i readonly`
normal

```
readOnly: true
```

fixed

```
f:readOnlyRootFilesystem: {}
      readOnlyRootFilesystem: true
      readOnly: true
```

test by using command
(we can't)

```
kubectl exec -it [POD_NAME] -- touch /etc/hello
```

(we can)

```
kubectl exec -it [POD_NAME] -- touch /tmp/hello
```
