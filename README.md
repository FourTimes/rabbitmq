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
