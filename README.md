# Microservice System Architecture

This project demonstrates a modern microservice system architecture, designed for scalability, maintainability, and resilience. The system is structured into several independent services, each responsible for a specific business domain, and communicates through well-defined APIs and asynchronous messaging.

## Architecture Overview

The architecture consists of the following main layers:

### 1. Client Layer
- **Web and Mobile Applications**: Serve as the single entry point for users to interact with the system.
- All requests are routed through the API Gateway for unified access and security.

### 2. API Gateway
- **Authentication**: Handles authentication for every client request.
- **Governance**: Implements rate limiting, routing, and monitoring.
- **Load Balancing**: Distributes traffic efficiently across microservices.

### 3. Microservices
- Each microservice is independent and responsible for a specific business function (e.g., Auth, Product, Order, Payment, Notification).
- Services communicate asynchronously using a Message Broker (e.g., RabbitMQ), enabling event-driven workflows.
- **Example**: When an order is created, the Order Service sends an event to the Notification Service via the message queue.

### 4. Database Layer
- Each microservice manages its own database, ensuring data isolation and autonomy.
- **PostgreSQL** is used for transactional data (e.g., orders, payments).
- **MongoDB** is used for unstructured data (e.g., user profiles, notifications).

### 5. Infrastructure
- Includes message brokers (RabbitMQ), service discovery (Consul), monitoring (Prometheus), and logging (ELK Stack).

## System Diagram

Below are visual representations of the system architecture:

### Main Architecture Diagram

![Microservice Architecture](./microservice.png)

### Alternative View

![Microservice Architecture 2](./microservice02.png)

### Professional Diagram

![Professional Microservice Diagram](./micropro.png)

### Mermaid Diagram (JPG)

![Mermaid Diagram](./microserviceMermaid.jpg)

### AI-Generated Diagram

![AI-Generated Microservice Diagram](./microservicePhindAI.jpg)

## Mermaid Syntax Diagram

```mermaid
graph TD
    subgraph Client Layer
        A[Client App]
    end

    subgraph Gateway Layer
        B[API Gateway]
    end

    subgraph Auth
        C[Auth Service]
    end

    subgraph Services
        D[User Service]
        E[Order Service]
        F[Product Catalog Service]
        G[Inventory Service]
        H[Payment Service]
        I[Notification Service]
    end

    subgraph Infra
        J[(RabbitMQ)]
        K[(Consul)]
        L[(Prometheus)]
        M[(ELK Stack)]
    end

    subgraph Databases
        DDB[(UserDB)]
        EDB[(OrderDB)]
        FDB[(ProductDB)]
        GDB[(InventoryDB)]
        HDB[(PaymentDB)]
    end

    A --> B
    B --> C
    B --> D
    B --> E
    B --> F
    B --> G
    B --> H
    B --> I

    D --> DDB
    E --> EDB
    F --> FDB
    G --> GDB
    H --> HDB

    D --> J
    E --> J
    F --> J
    G --> J
    H --> J

    D --> K
    E --> K
    F --> K
    G --> K

    D --> L
    E --> L
    F --> L
    G --> L
    H --> L

    D --> M
    E --> M
    F --> M
``` 