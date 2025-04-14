# Kubernetes

En Kubernetes, puedes tener varios [[#Cluster|clúster]], y cada [[#Cluster|clúster]] está compuesto por un conjunto de [[#Nodo|nodos]]

En cada [[#Cluster|clúster]] de Kubernetes, hay un [[#Nodo|nodo]] maestro que es responsable de administrar y coordinar las operaciones del [[#Cluster|clúster]]. El [[#Nodo|nodo]] maestro es el punto central de control y toma decisiones sobre la programación, la asignación de recursos, el escalado y la monitorización de los nodos de trabajo. El [[#Nodo|nodo]] maestro se comunica con los [[#Nodo|nodos]] de trabajo para enviar instrucciones y recibir actualizaciones sobre el estado del [[#Cluster|clúster]].

Cada [[#Cluster|clúster]] de Kubernetes tiene uno o más [[#Nodo|nodos]] de trabajo (también conocidos como [[#Nodo|nodos]] esclavos), que son las máquinas en las que se ejecutan los [[#POD|pods]]. Los [[#Nodo|nodos]] de trabajo proporcionan el entorno de ejecución para los contenedores y son los responsables de ejecutar y mantener los [[#POD|pods]] en funcionamiento.

Dentro de cada [[#Nodo|nodo]] de trabajo, puedes tener uno o más [[#POD|pods]]. Cada [[#POD|pod]] es una instancia única de una o más aplicaciones que se ejecutan en el [[#Cluster|clúster]]. Los [[#POD|pods]] pueden contener uno o varios contenedores que comparten recursos y un entorno de ejecución común.

En resumen, en Kubernetes puedes tener múltiples [[#Cluster|clústeres]], cada uno con un [[#Nodo|nodo]] maestro que administra los [[#Nodo|nodos]] de trabajo. En cada [[#Nodo|nodo]] de trabajo, se ejecutan uno o más [[#POD|pods]] que contienen uno o varios contenedores. Esta estructura jerárquica y modular permite la gestión eficiente y escalable de aplicaciones en contenedores.

## Kubectl
- Create deployment
```shell
kubectl create deployment mysqldb --image=mysql:8 --port=3306
```

- Create configuration file
```shell
kubectl create deployment mysqldb --image=mysql:8 --port=3306 --dry-run=client -o yaml > deployment-mysql.yaml
```

- Create deployment from a yaml file
```shell
kubectl apply -f ./deployment-mysql.yaml
```

- Get list of resources
```shell
kubectl get pods
```

- Get list all resources
```shell
kubectl get al
```

- Describe the pod
```shell
kubectl describe pods <pod-name>
```

- Log the pod
```shell
kubectl log <pod-name>
```

- Get list of deployments
```shell
kubectl get deployment
```

- Delete deployment
```shell
kubectl delete deployment <deploy-name>
```

- Expose port
```shell
kubectl expose deployment mysqldb --port=3306 --type=ClusterIP
```
 > ClusterIP: Allows internal communication between pods
 > NodePort: Allows external communication through the public IP and port
 > LoadBalancer: Allows external communication through the public IP and port using the load balancer
