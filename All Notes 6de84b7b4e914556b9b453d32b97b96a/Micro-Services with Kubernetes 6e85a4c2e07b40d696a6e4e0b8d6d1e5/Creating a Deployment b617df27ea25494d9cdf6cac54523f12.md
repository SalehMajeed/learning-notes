# Creating a Deployment

### Creating a Deployment using YAML Configuration

In Kubernetes, a Deployment manages the deployment and scaling of pods. Below is an example YAML configuration for creating a Deployment:

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: posts-depl
spec:
  replicas: 1
  selector:
    matchLabels:
      app: posts
  template:
    metadata:
      labels:
        app: posts
    spec:
      containers:
        - name: posts
          image: stephengrider/posts:0.0.1
```

In this YAML configuration:

- **`apiVersion: apps/v1`** specifies the Kubernetes API version used for this resource.
- **`kind: Deployment`** indicates that we are defining a Deployment resource.
- **`metadata`** contains information about the deployment, such as its name.
- **`spec`** defines the desired state of the deployment.
- **`replicas: 1`** specifies that one replica (pod) of the application should be running.
- **`selector`** determines which pods the deployment will manage. In this case, it selects pods with the label **`app: posts`**.
- **`template`** defines the pod template used by the deployment.
    - **`metadata.labels`** assigns the label **`app: posts`** to the pods created by this deployment.
    - **`spec.containers`** specifies the containers within the pods.
        - **`name: posts`** assigns the name "posts" to the container.
        - **`image: stephengrider/posts:0.0.1`** specifies the Docker image to use for the container. In this example, it pulls the image "stephengrider/posts" with version "0.0.1".

To create the deployment, save this configuration in a file (e.g., **`mydeployment.yaml`**) and apply it using the **`kubectl apply -f`** command:

```yaml
kubectl apply -f mydeployment.yaml
```