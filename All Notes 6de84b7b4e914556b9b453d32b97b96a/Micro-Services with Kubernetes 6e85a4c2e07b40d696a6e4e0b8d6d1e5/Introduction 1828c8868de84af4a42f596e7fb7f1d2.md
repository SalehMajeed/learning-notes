# Introduction

# Definition of Micro-Services

Microservices is an architectural approach where a software application is structured as a collection of small, independent services that are designed to perform specific business functions. One key principle in microservices architecture is the concept of "Database Per Service."

## Database Per Service

In microservices, each individual service has its own dedicated database. For example:

- **User Service:** Manages user-related data such as profiles, authentication, and authorization in its own database.
- **Product Service:** Handles product-related information, pricing, and inventory in its dedicated database.
- **Order Service:** Maintains order history, shipping details, and payment information in its distinct database.

This separation ensures that each service has control over its data, reducing dependencies on other services' databases.

## Communication Strategies between Services

Microservices need to communicate with each other to fulfill the overall functionality of the application. There are two primary communication strategies:

### Synchronous Communication (Sync)

In synchronous communication, services directly interact with each other in real-time. For example:

- **User Service:** Calls the **Authentication Service** synchronously to verify user credentials before allowing access.
- **Order Service:** Requests product availability from the **Product Service** in real-time to update order status.

While synchronous communication can be efficient, it may lead to tight coupling between services.

### Asynchronous Communication (Async)

Asynchronous communication involves using events or message queues for communication between services. For example:

- **Product Service:** Publishes a product update event whenever inventory levels change.
- **Order Service:** Subscribes to product update events and asynchronously updates order statuses based on product availability changes.

This approach decouples services, allowing them to operate independently and providing more flexibility in scaling.

In summary, microservices architecture promotes the use of dedicated databases for each service, enforcing autonomy. Communication between services can be synchronous or asynchronous, with the latter providing greater flexibility and decoupling.