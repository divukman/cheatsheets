# K8s Cheat-sheet

* Switch from minikube to gcloud and back:
    ```
    You can switch from local (minikube) to gcloud and back with:
    kubectl config use-context CONTEXT_NAME
    to list all contexts:
    kubectl config get-contexts
    ```

* List namespaces:
    ```
    kubectl get namespaces
    ```

* Create namespace:
    ```
    kubectl create namespace <namespace name>
    ```

* Delete namespace:
    ```
    kubectl delete namespaces <namespace name>    
    ```

* Get name of the current namespace:
    ```
    kubectl config view --minify --output 'jsonpath={..namespace}'; echo
    ```

* Change the current namespace:
    ```
    kubectl config set-context --current --namespace=<NAME>
    ```

* Minikube, reuse docker daemon:

    ```
    eval $(minikube docker-env)
    ``` 

* Minkube dahsboard:
    ```
    minkube dashboard
    ``` 

* Create new deployment object:
    ```
    kubectl create deployment app-name --image=divukman/app-name
    ```

* Delete deployment:
    ```
    kubectl delete deployment app-image
    ```

* Get deployments on cluster:
    ```
    kubect get deployments
    ```

* Get pods:
    ```
    kubectl get pods
    ```

* Expose a deployment with a service
    ```
    kubectl expose deployment deployment-name --type=LoadBalancer --port=8080
    ```

* Get services:
    ```
    kubectl get services
    ```

* Minikube only: Return URL to connect to the service:
    ```
    minikube service service-name
    ```

* Scale deployment:
    ```
    kubectl scale deployment/deployment-name --replicas=3
    ```

* Update deployment:
    ```
    kubectl set image deployment/deployment-name container_name=divukman/app-name:tag
    ```

* Check deployment rollout status:
    ```
    kubectl rollout status deployment/deployment-name
    ```
    
* Rollback deployment:
    ```
    kubectl rollout undo deployment/deployment-name
    kubectl rollout undo deployment/deployment-name --to-revision=N
    ```
    
* View deployment rollout history:
    ```
    kubectl rollout history deployment/deployment-name
    kubectl rollout history deployment/deployment-name --revision=N
    ```
    
* Delete service:
    ```
    kubectl delete service service-name
    ```

* Delete deployment:
    ```
    kubectl delete deployment deployment-name
    ```

* Create configmap
    - Create a new configmap named my-config with keys for each file in folder bar
    ```
    kubectl create configmap my-config --from-file=path/to/bar
    ```

    - Create a new configmap named my-config with specified keys instead of names on disk
    ```
    kubectl create configmap my-config --from-file=ssh-privatekey=~/.ssh/id_rsa --from-file=ssh-publickey=~/.ssh/id_rsa.pub
    ```

    - Create a new configMap named my-config with key1=config1 and key2=config2
    ```
    kubectl create configmap my-config --from-literal=key1=config1 --from-literal=key2=config2
    ```

* Create a resource in a namespace:
    ```
    kubectl apply -f pod.yaml --namespace=test
    ```

* Delete a resource in a namespace:
    ```
    kubectl delete -f pod.yaml --namespace=test
    ```
    
* Create CronJob:
    ```
    kubectl create -f https://k8s.io/examples/application/job/cronjob.yaml
    ```

* Get jobs:
    ```
    kubectl get jobs --watch
    ```

* Delete cron job:
    ```
    kubectl delete cronjob hello
    ```
    
* Dump pod logs (stdout):
    ```
    kubectl logs my-pod
    ```   

## Helm


* Create a helm chart 
    ```
    helm create hello-world
    ```

* Lint, verify that your chart follows best practices 
    ```
    helm lint
    ```

* Dry run 
    ```
    helm install --dry-run --debug
    ```

* Package the chart to be able to distribute manually or through public or private chart repositories
    ```
    helm package ./hello-world
    Successfully packaged chart and saved it to: \hello-world\hello-world-0.1.0.tgz 
    ```

* Auth: 
   - Create service account with Artifact Registry role, create JSON key.
    ```
    cat /path/to/key/my_sa_key.json | helm registry login -u _json_key --password-stdin https://europe-west2-docker.pkg.dev
    ```

* Push packaged artifact to Artifact Registry 
    ```
    helm push my-chart-0.1.0.tgz oci://LOCATION-docker.pkg.dev/PROJECT/REPOSITORY
    ```

    
    



