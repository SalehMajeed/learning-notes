# Load Balancing & Ingress

### **Load Balancer Service vs. Ingress (Ingress Controller)**

### Load Balancer Service:

- **Purpose:**
    - A Load Balancer Service is used to expose a service to the external world and distribute incoming traffic among the pods of the service.
    - It is primarily used when running a Kubernetes cluster in a cloud environment (like AWS, Azure, or Google Cloud) where cloud providers offer load balancer services.
- **Type:**
    - It is a type of Kubernetes Service (**`ServiceType: LoadBalancer`**).
- **External IP:**
    - Automatically provisions an external IP address that directs traffic to the service.
- **Usage:**
    - Suitable for exposing services externally, especially in a production environment.
    - Provides a stable external IP address for the service.
- **Configuration:**
    - Requires minimal configuration in the service definition.
- **Example YAML:**
    
    ```yaml
    yamlCopy code
    apiVersion: v1
    kind: Service
    metadata:
      name: my-service
    spec:
      selector:
        app: my-app
      ports:
        - protocol: TCP
          port: 80
          targetPort: 8080
      type: LoadBalancer
    
    ```
    

### Ingress (Ingress Controller):

- **Purpose:**
    - Ingress is an API object that manages external access to services within a cluster. It allows you to define rules for routing external HTTP and HTTPS traffic to services based on the request's hostname or path.
- **Type:**
    - Ingress is not a service type but a resource that works with an Ingress Controller.
- **External IP:**
    - Does not automatically provision an external IP address. Requires an Ingress Controller to handle external traffic.
- **Usage:**
    - Suitable for more complex routing scenarios, path-based routing, and managing multiple services with a single external IP.
    - Often used with Ingress Controllers (e.g., NGINX Ingress, Traefik) that implement the Ingress rules.
- **Configuration:**
    - Requires defining Ingress resources with rules specifying how traffic should be directed.
    - Requires an Ingress Controller to interpret and apply Ingress rules.
- **Example YAML:**
    
    ```yaml
    yamlCopy code
    apiVersion: networking.k8s.io/v1
    kind: Ingress
    metadata:
      name: my-ingress
    	annotations:
        kubernetes.io/ingress.class: nginx
    spec:
      rules:
      - host: mydomain.com
        http:
          paths:
          - path: /
            pathType: Prefix
            backend:
              service:
                name: my-service
                port:
                  number: 80
    
    ```
    

### Summary:

- **Load Balancer Service:**
    - Simpler setup.
    - Automatically provisions an external IP.
    - Suitable for basic external access.
- **Ingress (Ingress Controller):**
    - More advanced routing capabilities.
    - Requires an Ingress Controller.
    - Suitable for managing complex routing scenarios and multiple services.