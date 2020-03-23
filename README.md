# kuber-study

## Description
Kubernetes playground

## Commands example

#### Creating POD
`kubectl create -f src/templates/pod-definition.yml`

#### To edit POD definition
`kubectl get pod <pod-name> -o yaml > pod-definition.yaml` \
`kubectl apply -f pod-definition.yaml` \
`kubectl edit pod <pod-name>` only for props
