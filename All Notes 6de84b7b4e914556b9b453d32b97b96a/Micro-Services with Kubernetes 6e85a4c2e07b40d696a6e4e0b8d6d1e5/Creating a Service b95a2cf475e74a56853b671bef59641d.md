# Creating a Service

### Creating a Service using YAML Configuration

To expose and manage access to the pods in a Kubernetes cluster, you can define a Service. Below is an example YAML configuration for creating a Service:

```yaml
apiVersion: v1
kind: Service
metadata:
  name: posts-srv
spec:
  type: NodePort
  selector:
    app: posts
  ports:
    - name: posts
      protocol: TCP
      port: 4000
      targetPort: 4000
```

In this YAML configuration:

- **`apiVersion: v1`** specifies the Kubernetes API version used for this resource.
- **`kind: Service`** indicates that we are defining a Service resource.
- **`metadata`** contains information about the service, such as its name.
- **`spec`** defines the desired state of the service.
- **`type: NodePort`** exposes the service on each node's IP at a static port, allowing external access.
- **`selector`** determines which pods the service will target. In this case, it selects pods with the label **`app: posts`**.
- **`ports`** specifies the ports on which the service will listen.
    - **`name: posts`** assigns the name "posts" to the service port.
    - **`protocol: TCP`** specifies the protocol used for the service.
    - **`port: 4000`** is the port on which the service will be accessible externally.
    - **`targetPort: 4000`** is the port on which the service will forward traffic to the pods.

To create the service, save this configuration in a file (e.g., **`myservice.yaml`**) and apply it using the **`kubectl apply -f`** command:

```yaml
kubectl apply -f myservice.yaml
```

This will create a service named "posts-srv" that exposes pods with the label **`app: posts`** on each node's IP at port 4000.