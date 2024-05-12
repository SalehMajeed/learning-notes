# Architecture Patterns

- **Listener:** Backend applications listen on a specific IP and port, creating a socket for connections.
- **Acceptor:** Accepts connections on the socket and returns a file descriptor representing the connection.
- **Reader (Worker):** Reads data sent to the connection, ensuring the buffer doesn't fill up and processing the TCP stream.

## Architecture Patterns on Managing Threads and Connections

### **1. Single Threaded Architecture**

- **Description:**
    - In a single-threaded architecture, a solitary thread is responsible for handling all connections and requests.
- **Example:**
    - A simple web server that sequentially processes incoming requests on a single thread. While easy to implement, it may limit scalability and responsiveness.

### **2. Multiple Threads Single Acceptor Architecture**

- **Description:**
    - Multiple threads handle incoming requests, and a single acceptor thread manages new connections.
- **Example:**
    - An application that employs a thread pool where each thread manages the processing of requests. Meanwhile, a single thread is dedicated to accepting new connections, distributing them to the available threads for further handling.

### **3. Multiple Threads Multiple Acceptors Architecture**

- **Description:**
    - This architecture involves multiple threads, each managing both requests and new connections. It aims to enhance concurrency and improve the system's responsiveness.
- **Example:**
    - A web server application where multiple threads are responsible for both accepting new connections and processing incoming requests concurrently. This approach can be more scalable than the single acceptor model.

### **4. Multiple Threads with Message-based Load Balancing Architecture**

- **Description:**
    - Load balancing is achieved by distributing messages (requests) among multiple threads through a message queue. Each thread processes a portion of the overall workload.
- **Example:**
    - An application using a message queue to distribute incoming tasks among multiple threads. Each thread independently processes messages from the queue, providing load balancing and concurrency.

### **5. Multiple Threads with Socket Sharding**

- **Description:**
    - Sockets, representing network connections, are distributed among multiple threads. Each thread is responsible for handling specific sockets, promoting parallelism.
- **Example:**
    - A high-performance network server that leverages socket sharding to distribute incoming connections among multiple threads. This approach helps avoid contention for a single thread, enhancing scalability.

These architecture patterns offer various trade-offs in terms of simplicity, scalability, and resource utilization. The choice depends on the specific requirements of the application and the desired balance between simplicity and performance.