# Kubernetes-1

Deploy an application with database in kubernetes

## Steps to orcesterate Mongodb service:

1. Set up databse service with mongosb
2. Set up mongo deployement and service that is running the mongo docker image
3. add mongo username and password in secrets file
4. pass in mongodp username and password to the deployment using env variables

## Steps to orcesterate webapp service:

1. create webapp service
2. pass in mongodp username and password to the webapp using env variables from secret file.
3. Make both services external: type: NodePort

## kubectl get pod

Final step: create all components one by one in kubernetes

1. create mongo config and secret: kubectl apply -f mongo-config.yaml and kubectl apply -f mongo-secret.yaml. here -f is for file

2. start database
   kubectl apply -f mongo.yaml

3. kubectl apply -f webapp.yaml

## Interating with k8s cluster

1. Get all components created in a cluster (deloyments, services and pods): kubectl get all
2. Get configmap: kubectl get configmap
3. get secrets: kubectl get secrets
4. details about components:
   describe service webapp-service or describe pod <pod-name>
5. check logs within pods: kubectl logs <pod-name>

## access webapp in browser

1. get the service name/port: kubectl get svc

which IP address?

run `minikube service <service-name>`
OR
NodePort service is always accessable at cluster nodes: in this case we only have one node minikube

2. get minikube internal ip: minikube ip or kubectl get node -o wide

3. open nodeIP:nodePort on webbrowser

"Note: currently I can't make the service to open on ip:port url"
