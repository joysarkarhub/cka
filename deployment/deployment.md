# Create a deployment 
kubectl create deploy dev-web --image=nginx:1.13.7-alpine

# Scale out a deployment
kubectl scale deployment dev-web --replicas=10

# Create a ghost deployment object from manifest
k create deploy ghost --image=ghost --dry-run -o yaml > ghost.yaml
k apply -f ghost.yaml --record

# Expose ghost to LoadBalancer
k expose deployment ghost --port 80 --target-port 80 --type LoadBalancer

# See deployment rollout history
k rollout history deploy ghost

# Rollback to previous version deployment
k rollout undo deployment ghost

# Rollback to a specefic version deployment
k rollout undo deployment ghost --to-revision=2

# Check the rollout status
k rollout status deployment ghost

# Puase the rollout of a deployment
k rollout puase deploy ghost

# Resume the rollout of a deployment
k rollout resume deploy ghost

# Set a minReadySeconds attribute to deployment 
k patch deployment ghost -p '{"spec": {"minReadySeconds": 10}}'

# Create a ReplicaSet

# Delete a replicSet but not the container
k delete rs nginx-rs --cascade=false

# Update the docker image
k set image ds nginx-ds nginx-ds-ctr=nginx:1.2.3
<<<<<<< HEAD

# How to see the image details in deployment
k rollout history deploy sampledeploy --revision=1
=======
kubectl --record deployment.apps/nginx-deployment set image deployment.v1.apps/nginx-deployment nginx=nginx:1.9.1

# Yaml for replicaset from k8s github 
https://github.com/kubernetes/website/blob/master/content/en/examples/controllers/frontend.yaml

# Pause a deployment
k rollout pause deploy sampledaploy

#Resume a deployment
k rollout resume deploy sampledaploy


>>>>>>> a6c8bbcd4cc0e05f3e37103c2779be56fc8ed9af



