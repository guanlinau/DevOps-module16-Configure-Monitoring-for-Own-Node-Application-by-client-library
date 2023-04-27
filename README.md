### Demo Project:

Configure Monitoring for Own Application

### Technologies used:

Prometheus, Kubernetes, Node.js, Grafana, Docker, Docker Hub

### Project Description:

1- Configure our NodeJS application to collect & expose Metrics with Prometheus Client Library

2- Deploy the NodeJS application, which has a metrics endpoint configured, into Kubernetes cluster

3- Configure Prometheus to scrape this exposed metrics and visualize it in Grafana Dashboard

### Usage instruction

###### Step 1: Configure node app

#1 Install nodejs client library: prom-client
#2 Create the logic to expose metrics with prometheus client library

###### Step 2: Build the node app image

#build node app image and push it to docker hub private repo

###### Step 3: Deploy node app to k8s cluster

#1 create secret for pulling image from docker hub private repo

```
kubectl create secret docker-registry my-registry-key \
> --docker-server=https://index.docker.io/v1/ \
> --docker-username=<username> \
> --docker-password=<your_password>
```

#2 create a config.yaml file to deploy node app into cluster

```
kubectl apply -f k8s-config.yaml
```

#3 Create servicemonitor.yaml to let prometheus pickup the node as a new target to collect node matrics
![image](images/Screenshot%202023-04-27%20at%205.40.52%20pm.png)

####### Step 4: Configure prometheus ui and grafana ui dashboard for new target: node
![image](images/Screenshot%202023-04-27%20at%205.59.18%20pm.png)
