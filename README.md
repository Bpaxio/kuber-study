# kuber-study

## Description
Kubernetes playground

## Commands example
`kubectl run `
`kubectl get all` - get info about all kubernetes components in cluster

#### Namespace
`kubectl create -f namespace-definition.yml` \
`kubectl create namespace dev` \
`kubectl config set-context $(kubectl config current-context) --namespace=dev` - set another namespace as default \
`kubectl get pods --all-namespaces` 
##### Resource Quota
It's required to limit resources of namespaces
`kubectl create -f rq-definition.yml`

#### POD
`kubectl create -f pod-definition.yml` \
`kubectl get pods --namespace=default` \
`kubectl delete pod ${name:myapp}` \
##### To edit POD definition
`kubectl get pod <pod-name> -o yaml > pod-definition.yml` \
`kubectl apply -f pod-definition.yml` \
`kubectl edit pod <pod-name>` only for props

#### ReplicaSet
`kubectl create -f rs-definition.yml` \
`kubectl get replicaset` \
`kubectl delete replicaset ${name:myapp-rs}`

##### Scale number of PODs
1) modify and run `kubectl replace -f rs-definition.yml`
2) `kubectl scale --replicas=6 -f rs-definition.yml` (not modified def file)
3) `kubectl scale --replicas=6 -f ${type:replicaset} ${name:myapp-rs}` (not modified def file)

#### Deployment
`kubectl create -f deployment-definition.yml` \
`kubectl get deployment` \
`kubectl delete deployment ${name:myapp-deployment}`

#### ConfigMap
1)  Imperative way
    ```shell script
    kubectl create configmap \
    <config-map-name> --from-literal=APP_COLOR=blue \
                      --from-literal=APP_MOD=dev
     ```
1) Declarative way
    ```shell script
    kubectl create configmap \
    <config-map-name> --from-file=<path-to-file>
    ```
    ```shell script
    kubectl create configmap \
    app-config --from-file=app-config-map.yaml
    ```



#### Imperative commands
1) Create an NGINX Pod \
    `kubectl run --generator=run-pod/v1 nginx --image=nginx`
1) Generate POD Manifest YAML file (-o yaml). Don't create it(--dry-run) \
    `kubectl run --generator=run-pod/v1 nginx --image=nginx --dry-run -o yaml`
1) Create a deployment \
    `kubectl create deployment --image=nginx nginx`
1) Generate Deployment YAML file (-o yaml). Don't create it(--dry-run) \
    `kubectl create deployment --image=nginx nginx --dry-run -o yaml` \
    `kubectl create deployment --image=nginx nginx --dry-run --replicas=4 -o yaml > nginx-deployment.yaml`

More about [generators](https://kubernetes.io/docs/reference/kubectl/conventions/#generators) \
`-o` specifies format of output. See [docs#output-options](https://kubernetes.io/docs/reference/kubectl/overview/#output-options)
