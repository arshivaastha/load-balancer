
# Spring Boot Load Balancer

This project demonstrates the implementation of a basic load balancer in Java Spring Boot. The load balancer supports two types of load balancing algorithms: **Round Robin** and **IP Hash**. This application is designed to be scalable, fault-tolerant, and robust.

## Project Structure

The project is structured as follows:

```
src/
├── main/
│   ├── java/
│   │   └── com/
│   │       └── load/
│   │           └── balancer/
│   │               ├── BalancerApplication.java
│   │               ├── config/
│   │               │   ├── LoadBalancerConfig.java
│   │               ├── service/
│   │               │   ├── LoadBalancerService.java
│   │               │   ├── RoundRobinLoadBalancer.java
│   │               │   ├── IPHashLoadBalancer.java
│   └── resources/
│       └── application.yml
└── test/
    └── java/
        └── com/
            └── load/
                └── balancer/
                    └── BalancerApplicationTests.java
```

## Code Explanation

### 1. BalancerApplication.java
This is the main entry point for the Spring Boot application.

- `@SpringBootApplication`: Marks the main class of the Spring Boot application, enabling auto-configuration and component scanning.
- `SpringApplication.run(BalancerApplication.class, args);`: Launches the Spring Boot application.

### 2. LoadBalancerConfig.java
This configuration class sets up the load balancing strategies.

- `@Configuration`: Indicates that the class can be used by the Spring IoC container as a source of bean definitions.
- `@Bean`: Marks methods that produce beans to be managed by Spring.

### 3. LoadBalancerService.java
This interface defines the contract for different load balancing strategies.

- `getServer(List<String> servers)`: Method signature for selecting a server from a list.

### 4. RoundRobinLoadBalancer.java
Implements the Round Robin load balancing algorithm.

- Uses `AtomicInteger` to manage the current position in the server list.

### 5. IPHashLoadBalancer.java
Implements the IP Hash load balancing algorithm.

- Hashes the client's IP address to determine the server index.

### 6. application.yml
Contains the configuration for the Spring Boot application.

- `server.port`: Configures the server to run on port 8080.
- `spring.cloud.loadbalancer.instances`: Defines the backend instances for load balancing.

## Running the Application

### Steps to Run
1. **Build the Project**:
   ```bash
   ./gradlew clean build
   ```
2. **Run the Application**:
   ```bash
   ./gradlew bootRun
   ```
   