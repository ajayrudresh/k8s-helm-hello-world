# k8s-helm-hello-world

## Prerequisities
1. Helm v3 and kubectl client tools should be installed
2. Kubernetes cluster

## Deploy Hello-Word App on Kubernetes using Helm Charts

1. Clone the helm chart

```shell
$ git clone https://github.com/ajayrudresh/k8s-helm-hello-world.git
```

2. Login to Kubernetes and create a namespace called helm-demo
```shell
$ kubectl create ns helm-demo
```

3. Deploy the helm chart on k8s helm-demo namespace
```shell
$ helm upgrade --install  bbg hello-world/ -n helm-demo
```

4. Verify the chart and created k8s resources
```shell
$ helm list -n helm-demo
NAME    NAMESPACE       REVISION        UPDATED                                 STATUS          CHART                   APP VERSION
bbg     helm-demo       1               2021-07-21 11:05:53.250927434 -0400 EDT deployed        hello-world-0.1.0       1.16.0
```

```shell
$ kubectl --namespace helm-demo get all
NAME                                   READY   STATUS    RESTARTS   AGE
pod/bbg-hello-world-5595bd8f8c-hg2xj   1/1     Running   0          13m

NAME                      TYPE           CLUSTER-IP      EXTERNAL-IP                                                              PORT(S)        AGE
service/bbg-hello-world   LoadBalancer   10.100.143.63   a6c445ab9482949d4a9f7e491cc4647a-541970909.us-east-2.elb.amazonaws.com   80:30736/TCP   13m

NAME                              READY   UP-TO-DATE   AVAILABLE   AGE
deployment.apps/bbg-hello-world   1/1     1            1           13m

NAME                                         DESIRED   CURRENT   READY   AGE
replicaset.apps/bbg-hello-world-5595bd8f8c   1         1         1       13m
```

5. Access the application using the LB URL
![](https://github.com/ajayrudresh/k8s-helm-hello-world/blob/main/contents/bbg-helm.PNG)



