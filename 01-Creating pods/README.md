# Creating pods

## 1. Using kubectl

We can create a pod using kubectl.

kubectl run [podname] --image=[image name]

For example, run the nginx:alpine container in a Pod

```shell
$ kubectl run myngnix --image=nginx:alpine

kubectl run --generator=deployment/apps.v1 is DEPRECATED and will be removed in a future version. Use kubectl run --generator=run-pod/v1 or kubectl create instead.
deployment.apps/myngnix created
```

We must use the new alternative suggested in the message


![Nginx started](../images/002.png)

## 2. kubectl get command

The kubectl get command can be used to retrieve information about Pods and many other Kubernetes objects.

List only Pods

```shell
$ kubectl get pods

NAME                       READY   STATUS    RESTARTS   AGE
myngnix-7d48fd4f6b-7s6hz   1/1     Running   0          6m57s

```

List all resources

```shell
$ kubectl get all


NAME                           READY   STATUS    RESTARTS   AGE
pod/myngnix-7d48fd4f6b-7s6hz   1/1     Running   0          7m33s

NAME                 TYPE        CLUSTER-IP   EXTERNAL-IP   PORT(S)   AGE
service/kubernetes   ClusterIP   10.96.0.1    <none>        443/TCP   72m

NAME                      READY   UP-TO-DATE   AVAILABLE   AGE
deployment.apps/myngnix   1/1     1            1           7m33s

NAME                                 DESIRED   CURRENT   READY   AGE
replicaset.apps/myngnix-7d48fd4f6b   1         1         1       7m33s

```

## 3. Expose a Pod Port

Pods and containers are only accesible within the Kubernetes cluster by default

One way to expose a container port externally: kubectl port-forward

kubectl port-forward [name-of-pod] 8080:80

```shell
$ kubectl port-forward myngnix-7d48fd4f6b-7s6hz 8080:80
```

Accesing using the browser at http://localhost:8080 we can see the welcome page of nginx.

![Nginx welcome page](../images/003.png)

8080 is the external port, and 80 the internal port. Is similar as docker.

## 4. Deleting a Pod

Running a Pod will cause a deployment to be created.

To delete a Pod use kubectl delete pod or find the deployment and use kubectl delete deployment.

```shell
$ kubectl delete pod myngnix-7d48fd4f6b-7s6hz
```

An then, the pod sudden will back to live!

We need to delete the deployment that manages the Pod

kubectl delete [name-of-deployment]

```shell
$ kubectl delete deployment.apps/myngnix
deployment.apps "myngnix" deleted
```

