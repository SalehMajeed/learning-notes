# Architecture of NGINX

NGINX follows a unique architecture designed for efficient handling of web server tasks. The architecture involves a master process, worker processes, and interaction with the underlying kernel. Here's a breakdown:

```markdown
 	+-----------------------+
  |   Master Process      |
  |                       |
  |   +-------------------+
  |   | Worker Process w1 |
  |   +-------------------+
  |   | Worker Process w2 |
  |   +-------------------+
  |   | Worker Process w3 |
  |   +-------------------+
  |                       |
  |       Kernel          |
  +-----------------------+

```

- **Master Process:**
    - The master process is responsible for overseeing the entire NGINX system. It manages the configuration, coordinates processes, and handles signals. The master process is not involved in serving client requests directly.
- **Spins up a worker process per CPU core by default:**
    - NGINX's default behavior is to create a worker process for each available CPU core. This approach maximizes parallelism and performance, as each worker process can handle its set of tasks independently.
- **Worker Processes (w1, w2, w3):**
    - Worker processes are responsible for serving client requests. Each worker process operates independently, capable of handling multiple connections simultaneously. This parallel processing ensures efficient utilization of system resources.
- **Child Process:**
    - The worker processes collectively form the child processes of the master. They execute the tasks assigned by the master process, responding to client requests, and managing connections.
- **Kernel:**
    - The kernel represents the core of the operating system. NGINX interacts with the kernel to perform essential tasks such as network communication, file I/O, and process management. The kernel acts as an interface between NGINX and the underlying hardware.

**Example:**
Consider an NGINX setup on a server with four CPU cores. The master process, like a supervisor, oversees the entire operation. It spawns four worker processes (w1, w2, w3), each assigned to a specific CPU core. These worker processes independently handle incoming client requests, distributing the load and maximizing the server's performance.

In summary, NGINX's architecture, with a master process and worker processes per CPU core, is designed for scalability and efficiency in serving concurrent client requests. This structure enables NGINX to harness the power of multicore systems effectively.