# rabbitmq


Operator Installtion

```bash

  # kubectl apply -f https://github.com/rabbitmq/cluster-operator/releases/latest/download/cluster-operator.yml
  
  namespace/rabbitmq-system created
  customresourcedefinition.apiextensions.k8s.io/rabbitmqclusters.rabbitmq.com created
  serviceaccount/rabbitmq-cluster-operator created
  role.rbac.authorization.k8s.io/rabbitmq-cluster-leader-election-role created
  clusterrole.rbac.authorization.k8s.io/rabbitmq-cluster-operator-role created
  rolebinding.rbac.authorization.k8s.io/rabbitmq-cluster-leader-election-rolebinding created
  clusterrolebinding.rbac.authorization.k8s.io/rabbitmq-cluster-operator-rolebinding created
  deployment.apps/rabbitmq-cluster-operator created
  
```



RabittMQ cluster yaml file

```yml
# vim rabbit-cluster.yml

apiVersion: rabbitmq.com/v1beta1
kind: RabbitmqCluster
metadata:
  name: rabbitmq-cluster
spec:
  replicas: 3
  persistence:
   storageClassName: tispring
   storage: 50Gi
  resources:
    requests:
      cpu: 100m
      memory: 0.4Gi
    limits:
      cpu: 100m
      memory: 0.5Gi


```


RabbitMQ cluster installtion


```bash

kubectl create ns queue
kubectl apply -f rabbit-cluster.yml -n queue

```

login details

```bash

# user Details
kubectl get secret rabbitmq-cluster-default-user -n queue -o jsonpath='{.data.username}' | base64 --decode

# Password Details
kubectl get secret rabbitmq-cluster-default-user -n queue -o jsonpath='{.data.password}' | base64 --decode

```


UI access


```bash

 kubectl port-forward --address 0.0.0.0 svc/rabbitmq-cluster 15672 -n queue

```
