# kuber-study

## Description
Kubernetes playground

## Commands example
#### POD
`kubectl create -f pod-definition.yml` \
`kubectl get pods` \
`kubectl delete pod ${name:myapp}` \
##### To edit POD definition
`kubectl get pod <pod-name> -o yaml > pod-definition.yml` \
`kubectl apply -f pod-definition.yml` \
`kubectl edit pod <pod-name>` only for props

#### ResplicaSet
`kubectl create -f rs-definition.yml` \
`kubectl get replicaset` \
`kubectl delete replicaset ${name:myapp-rs}`

##### Scale number of PODs
1) modify and run `kubectl replace -f rs-definition.yml`
2) `kubectl scale --replicas=6 -f rs-definition.yml` (not modified def file)
3) `kubectl scale --replicas=6 -f ${type:replicaset} ${name:myapp-rs}` (not modified def file)
