# What is Kubernetes

## Kubernetes

Kubernetes (K8s) and Docker serve different purposes in the world of container orchestration.

- **Docker:** A containerization platform that allows developers to package applications and their dependencies into a single container.
- **Kubernetes:** An orchestration platform that automates the deployment, scaling, and management of containerized applications.

## What is kubectl and minikube

- **kubectl:** The command-line tool for interacting with a Kubernetes cluster. It allows users to deploy and manage applications on Kubernetes.
- **minikube:** A tool that enables you to run a single-node Kubernetes cluster locally for development and testing purposes. It's a lightweight, easy-to-install solution.

## Key Kubernetes Concepts

1. **Kubernetes Cluster:** A collection of nodes (virtual machines) and a master that manages the entire cluster.
2. **Node:** A virtual machine that forms part of the Kubernetes cluster.
3. **Pod:** The smallest deployable unit in Kubernetes, wrapping up a container or multiple containers.
4. **Deployment:** A Kubernetes resource that reads a configuration file and is responsible for managing pods.
5. **Service:** Manages the networking for different microservices within the cluster.
6. **Master:** The central controlling unit of a Kubernetes cluster, responsible for managing and coordinating all activities.

## Types of Services

1. **Cluster IP:** Exposes pods in the cluster with an easily accessible URL within the cluster.
2. **Node Port:** Accesses pods outside of the cluster, using a specific port on each node.
3. **Load Balancer:** Similar to Node Port but with automatic load balancing, making it a more suitable approach for production.
4. **External Name:** Redirects in-cluster requests to a CNAME (Canonical Name) URL.

## Kubernetes Commands

1. `kubectl get pods`: Lists all pods in the cluster.
    
    ```bash
    kubectl get pods
    
    ```
    
2. `kubectl exec -it [pod_name] [cmd]`: Executes a command in a given container within a pod interactively.
    
    ```bash
    kubectl exec -it mypod -- /bin/bash
    
    ```
    
3. `kubectl logs [pod_name]`: Prints out logs for a given pod.
    
    ```bash
    kubectl logs mypod
    
    ```
    
4. `kubectl delete pod [pod_name]`: Deletes a specific pod.
    
    ```bash
    kubectl delete pod mypod
    
    ```
    
5. `kubectl apply -f [config_file_name]`: Runs the configuration specified in the file.
    
    ```bash
    kubectl apply -f myconfig.yaml
    
    ```
    
6. `kubectl describe pod [pod_name]`: Provides detailed information about a running pod.
    
    ```bash
    kubectl describe pod mypod
    
    ```
    
7. `kubectl get deployments`: Lists all deployments in the cluster.
    
    ```bash
    kubectl get deployments
    
    ```
    
8. `kubectl describe deployment [depl name]`: Offers details about a specific deployment.
    
    ```bash
    kubectl describe deployment mydeployment
    
    ```
    
9. `kubectl delete deployment [depl_name]`: Deletes a particular deployment.
    
    ```bash
    kubectl delete deployment mydeployment
    
    ```
    

These commands, along with examples, are essential for managing and interacting with Kubernetes clusters and applications.