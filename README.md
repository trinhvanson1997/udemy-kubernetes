Learn k8s: https://www.youtube.com/watch?v=X48VuDVv0do&t=10s


### What is kubernetes?

- Open source container orchestration tool
- Manage containerized applications in different deployment environments (physical, virtual, cloud)

### What problems does K8S solve?

- Trend from **Monolith** to **Microservices**
- Increase usage of containers


### What features do orchestration tools offer?

- High availability: has no downtime
- Scalability: high performance
- Disaster recovery: backup and restore data

---
# Kubernetes Components

### Pod
- Smallest unit of K8s
- Abstraction over container
- Usually 1 application per Pod
- Each pod gets its own IP address
- New IP address on re-creation

### Service
- Permanent IP address
- Lifecycle of Pod and Service not connected. If pod is die, service still alive

### ConfigMap
- Save environment variables

### Secrets
- Store secret data
- Encode data by base64

### Volumes

### Ingress

### Deployments

### StatefulSet
- is used for stateful application like database


# Kubernetes Architecture

4 processes run on every master node:

- Api Server: interact with k8s via a dashboard, apis, validate requests
- Scheduler: decides on which Node new Pod should be scheduled
- Controller manager: detects cluster state changes, eg: if pod dies, controller will try to recover the pod
- etcd: key value holds the current status of any K8s components

## 3 parts of configuration file

- metadata:
- spec:
- status: get from etcd



# Organizing components with K8s Namespace

### What is Namespace?

4 Namespaces per Default
- default: this is default namespace

- kube-node-lease:
    - heartbeats of nodes
    - each node has associated lease object in namespace
    - determines the availability of a node

- kube-public:
    - publicly accessible data
    - a configmap, which contains cluster information
  
- kube-system:
    - do NOT create or modify in kube-system
    - system processes
    - master and kubectl processes
    

### Why to use Namespace?

- Resources grouped in Namespaces
- Conflicts: many teams, same application (eg: same name project)
- Resource sharing: (eg: there are both staging and development in a cluster)
- Access and resource limits on namespaces: 
      - each team has own, isolated environment
    - limit cpu, ram, storage per NS
    
### command

```
create: kubectl create namespace <name>
```

# Ingress
