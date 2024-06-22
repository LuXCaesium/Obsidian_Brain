---
created: 2024-01-15 21:04
tags:
  - "#MLOps"
---

# Kubernetes

Kubernetes is a production-ready, open source container orchestration package. It enables containerised applications to be available 24/7 and manage the resource the application has access to.

### Kubernetes Clusters
Kubernetes will coordinate highly available clusters which are connected to work together. It will automate the distribution and scheduling of the application container across a cluster of many machines.

A cluster will consist of two types of resource:
- The **Control Plane** which coordinates the cluster
- **Nodes** are the workers that run applications. 

![[Kubernetes_Cluster.svg]]
The **Control Plane** is responsible for managing the cluster such as:
scheduling applications, maintaining applications state, scaling and rolling out new updates.

A **Node** is a VM or a physical computer that serves as a worker machine. Each node has a **Kubelet** which is an agent to communicate with the control plane. The node also has tools for handling container operations, such as [[containerd]] or [[CRI-O]].

As a rule, a production setup should have at least 3 nodes.

When deploying an application, you tell the control plane to start it which will then be scheduled on the nodes. Minikube is an example of a single node kubernetes implementation.

### Kubernetes Deployments

A kubernetes **Deployment** instructs kubernetes how to create and update instances of the app. The control plane schedules the app instances included in the deployment to run on individual nodes in the cluster

Kubernetes Deployment controller continuously monitors the app instance, so if a node goes down a new instance is created on a new node.

![[Kubernetes_Deployment.svg]]