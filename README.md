# Kubernetes Nedir?
Container (konteyner) tabanlı uygulamaları yöneten, dağıtan ve ölçeklendiren kullanılan popüler bir açık kaynaklı container orchestration (konteyner yönetimi) sistemidir.

## Kubernetes Core Concepts
- [Pod](https://github.com/hamity1ld1r1m/Kubernetes-Nedir/blob/main/01_Kubernetes_Core_Concepts/pod.yaml)
- [Labels & Selectors](https://github.com/hamity1ld1r1m/Kubernetes-Nedir/blob/main/01_Kubernetes_Core_Concepts/label.yaml)
- [ReplicaSet](https://github.com/hamity1ld1r1m/Kubernetes-Nedir/blob/main/01_Kubernetes_Core_Concepts/replicaset.yaml)
- [Deployment](https://github.com/hamity1ld1r1m/Kubernetes-Nedir/blob/main/01_Kubernetes_Core_Concepts/recrate-deployment.yaml)
- [Rolling Updates – Rollbacks](https://github.com/hamity1ld1r1m/Kubernetes-Nedir/blob/main/01_Kubernetes_Core_Concepts/rollingupdate-deployment.yaml)
- [ClusterIP Service](https://github.com/hamity1ld1r1m/Kubernetes-Nedir/blob/main/01_Kubernetes_Core_Concepts/clusterip-svc.yaml)
- [NodePort Service](https://github.com/hamity1ld1r1m/Kubernetes-Nedir/blob/main/01_Kubernetes_Core_Concepts/nodeport-svc.yaml)
- [Namespaces](https://github.com/hamity1ld1r1m/Kubernetes-Nedir/blob/main/01_Kubernetes_Core_Concepts/namespaces.yaml)
- [Liveness Probe](https://github.com/hamity1ld1r1m/Kubernetes-Nedir/blob/main/01_Kubernetes_Core_Concepts/liveness.yml)
- [Readiness Probe](https://github.com/hamity1ld1r1m/Kubernetes-Nedir/blob/main/01_Kubernetes_Core_Concepts/readiness.yml)

## Scheduling
- [DaemonSets](https://github.com/hamity1ld1r1m/Kubernetes-Nedir/blob/main/02_Scheduling/daemonset.yaml)
- [Node Selectors](https://github.com/hamity1ld1r1m/Kubernetes-Nedir/blob/main/02_Scheduling/nodeselector.yaml)
- [Node Affinity](https://github.com/hamity1ld1r1m/Kubernetes-Nedir/blob/main/02_Scheduling/node-affinity.yml)
- [Pod Affinity](https://github.com/hamity1ld1r1m/Kubernetes-Nedir/blob/main/02_Scheduling/pod-affinity.yml)
- [Resource Requirements & Limits](https://github.com/hamity1ld1r1m/Kubernetes-Nedir/blob/main/02_Scheduling/resource-limited-pod.yaml)
- [Tolerations](https://github.com/hamity1ld1r1m/Kubernetes-Nedir/blob/main/02_Scheduling/tolerated-pod.yml)
- [Static Pods](https://github.com/hamity1ld1r1m/Kubernetes-Nedir/blob/main/02_Scheduling/staticpod.yaml)
- [Schedule Pod](https://github.com/hamity1ld1r1m/Kubernetes-Nedir/blob/main/02_Scheduling/schedule-pod.yaml)

## Logging & Monitoring
- [Metric Server](https://github.com/hamity1ld1r1m/Kubernetes-Nedir/blob/main/03_Logging_&_Monitoring/metricserver.md)

## Application Lifecycle Management
- [Commands & Arguments](https://github.com/hamity1ld1r1m/Kubernetes-Nedir/blob/main/04_Application_Lifecycle_Management/commands-args.yaml)
- [Environment Variables](https://github.com/hamity1ld1r1m/Kubernetes-Nedir/tree/main/04_Application_Lifecycle_Management/ENV(Environment%20Variables))
- [Init Containers](https://github.com/hamity1ld1r1m/Kubernetes-Nedir/blob/main/04_Application_Lifecycle_Management/initcontainer.yaml)
- [MultiContainer Pods](https://github.com/hamity1ld1r1m/Kubernetes-Nedir/blob/main/04_Application_Lifecycle_Management/multicontainer.yaml)
- [Security](https://github.com/hamity1ld1r1m/Kubernetes-Nedir/tree/main/04_Application_Lifecycle_Management/security)

## Cluster Maintenance
- [Cluster Upgrade](https://github.com/hamity1ld1r1m/Kubernetes-Nedir/blob/main/05_Cluster_Maintenance/Cluster-Upgrade-(Master-Node-Worker-Node).md)
- [ETCD Backup](https://github.com/hamity1ld1r1m/Kubernetes-Nedir/blob/main/05_Cluster_Maintenance/ETCD-BACKUP.md)
- [YAML Backup](https://github.com/hamity1ld1r1m/Kubernetes-Nedir/blob/main/05_Cluster_Maintenance/.yaml-backup.md)

## Security
- [CSR & RBAC ile Authentication & Authorization](https://github.com/hamity1ld1r1m/Kubernetes-Nedir/blob/main/06_Security/CSR&BAC-ile-Authentication&Authorization.md)
- [Cluster Roles & RoleBindings](https://github.com/hamity1ld1r1m/Kubernetes-Nedir/tree/main/06_Security/Cluster%20Roles%20&%20RoleBindings%20with%20Service%C2%A0Accounts)
- [Network Policy](https://github.com/hamity1ld1r1m/Kubernetes-Nedir/tree/main/06_Security/Network%20Policy)
- [Private Pod](https://github.com/hamity1ld1r1m/Kubernetes-Nedir/blob/main/06_Security/private-pod.yml)

## Storage
- [Volume](https://github.com/hamity1ld1r1m/Kubernetes-Nedir/tree/main/07_Storage/volume)
- [PersistentVolumes and Claims](https://github.com/hamity1ld1r1m/Kubernetes-Nedir/tree/main/07_Storage/pv&pvc)
- [Storage Class](https://github.com/hamity1ld1r1m/Kubernetes-Nedir/tree/main/07_Storage/storageclass)
- [Stateful Set](https://github.com/hamity1ld1r1m/Kubernetes-Nedir/tree/main/07_Storage/statefulset.yml)
- [Job](https://github.com/hamity1ld1r1m/Kubernetes-Nedir/tree/main/07_Storage/job.yml)
- [CronJob](https://github.com/hamity1ld1r1m/Kubernetes-Nedir/tree/main/07_Storage/cronjob.yml)
## Networking
- [DNS](https://github.com/hamity1ld1r1m/Kubernetes-Nedir/blob/main/08_Networking/dns.yaml)
- [Ingress](https://github.com/hamity1ld1r1m/Kubernetes-Nedir/blob/main/08_Networking/Ingress)
- [Helm & MetalLB](https://github.com/hamity1ld1r1m/Kubernetes-Nedir/blob/main/08_Networking/Ingress/Ingress-Kurulum.md)

## Daha Fazla Bilgi
- [Kubernetes Nedir? - Medium Makalesi](https://medium.com/@hamityldrm/kubernetes-nedir-b1baeebe211c)
