## 1. What is System Design?

### Answer

System Design is the process of designing scalable, reliable, maintainable, and efficient software systems.

### Goals

* Scalability
* Reliability
* Performance
* Maintainability
* Availability

---

## 2. Why is System Design important for Python developers?

### Answer

Python is widely used for:

* Backend Services
* APIs
* AI Systems
* Data Platforms
* MLOps Pipelines

System Design helps build production-ready applications.

---

## 3. What is Scalability?

### Answer

Scalability is the ability of a system to handle increasing workload.

### Types

```text
Vertical Scaling
Horizontal Scaling
```

---

## 4. What is Vertical Scaling?

### Answer

Adding more resources to a single machine.

### Example

```text
8 GB RAM
↓
32 GB RAM
```

---

## 5. What is Horizontal Scaling?

### Answer

Adding more servers.

### Example

```text
Server 1
Server 2
Server 3
```

---

## 6. What is High Availability?

### Answer

Ensuring the application remains operational even during failures.

### Example

```text
99.9%
99.99%
99.999%
```

---

## 7. What is Fault Tolerance?

### Answer

The ability to continue operating despite failures.

### Example

```text
Primary Server Fails
↓
Backup Server Takes Over
```

---

## 8. What is a Load Balancer?

### Answer

A Load Balancer distributes incoming requests across multiple servers.

### Flow

```text
Users
 ↓
Load Balancer
 ↓
Server A
Server B
Server C
```

---

## 9. Why use a Load Balancer?

### Answer

Benefits:

* Better Performance
* High Availability
* Scalability
* Failover

---

## 10. Common Load Balancers?

### Answer

Examples:

* Nginx
* HAProxy
* AWS ELB
* Traefik

---

## 11. What is Stateless Architecture?

### Answer

Each request contains all required information.

### Example

```text
Request 1
Independent

Request 2
Independent
```

---

## 12. Why are stateless services preferred?

### Answer

Benefits:

* Easier Scaling
* Simpler Deployment
* Better Reliability

---

## 13. What is State Management?

### Answer

Storage of user/session information across requests.

### Examples

* Redis
* Databases
* Session Stores

---

## 14. What is Caching?

### Answer

Storing frequently accessed data for faster retrieval.

### Goal

```text
Reduce Latency
```

---

## 15. Why is Caching important?

### Answer

Benefits:

* Faster Responses
* Reduced Database Load
* Better User Experience

---

## 16. What is Redis?

### Answer

Redis is an in-memory key-value store.

### Common Uses

* Cache
* Sessions
* Queues
* Rate Limiting

---

## 17. What is Cache Aside Pattern?

### Answer

Application checks cache first.

### Flow

```text
Request
 ↓
Cache
 ↓
Database
```

---

## 18. What is Write Through Cache?

### Answer

Data is written to cache and database simultaneously.

### Benefit

```text
Cache Always Updated
```

---

## 19. What is Write Back Cache?

### Answer

Data is written to cache first and later persisted.

### Benefit

```text
Higher Performance
```

---

## 20. What is a Database?

### Answer

A system that stores and manages application data.

### Examples

* PostgreSQL
* MySQL
* MongoDB

---

## 21. SQL vs NoSQL?

### Answer

| SQL        | NoSQL                |
| ---------- | -------------------- |
| Structured | Flexible             |
| ACID       | Eventual Consistency |
| Joins      | Document Based       |
| Relational | Non-Relational       |

---

## 22. What is Database Indexing?

### Answer

Indexes speed up data retrieval.

### Example

```sql
CREATE INDEX idx_email
ON users(email);
```

---

## 23. What is Database Sharding?

### Answer

Splitting data across multiple databases.

### Example

```text
Users A-M → Shard 1

Users N-Z → Shard 2
```

---

## 24. What is Database Replication?

### Answer

Copying data to multiple servers.

### Benefits

* High Availability
* Read Scaling

---

## 25. What System Design topics are most important for Python interviews?

### Answer

Frequently Asked:

* Scalability
* Load Balancers
* Caching
* Redis
* Databases
* Sharding
* Replication
* High Availability

---

## 26. What is an API?

### Answer

API (Application Programming Interface) allows communication between applications.

### Example

```text
Frontend
↓
API
↓
Backend
↓
Database
```

---

## 27. What is REST?

### Answer

REST (Representational State Transfer) is an architectural style for designing web services.

### Common Methods

```http
GET
POST
PUT
PATCH
DELETE
```

---

## 28. What is a RESTful API?

### Answer

An API that follows REST principles.

### Characteristics

* Stateless
* Resource-Based
* Uses HTTP Methods
* Cacheable

---

## 29. Difference Between PUT and PATCH?

### Answer

| PUT                      | PATCH                    |
| ------------------------ | ------------------------ |
| Replaces entire resource | Updates partial resource |
| Full update              | Partial update           |
| Idempotent               | Usually idempotent       |

---

## 30. What is GraphQL?

### Answer

GraphQL is a query language for APIs.

### Benefit

Clients request only required data.

### Example

```graphql
{
  user {
    name
    email
  }
}
```

---

## 31. REST vs GraphQL?

### Answer

| REST                  | GraphQL             |
| --------------------- | ------------------- |
| Multiple endpoints    | Single endpoint     |
| Fixed response        | Flexible response   |
| Overfetching possible | Exact data fetching |
| Simpler               | More powerful       |

---

## 32. What is API Versioning?

### Answer

Managing API changes without breaking clients.

### Example

```text
/api/v1/users
/api/v2/users
```

---

## 33. Why is API Versioning Important?

### Answer

Benefits:

* Backward Compatibility
* Safe Upgrades
* Easier Maintenance

---

## 34. What is Authentication?

### Answer

Authentication verifies identity.

### Example

```text
Username + Password
```

---

## 35. What is Authorization?

### Answer

Authorization determines permissions.

### Example

```text
User
Can Read

Admin
Can Read + Write
```

---

## 36. Authentication vs Authorization?

### Answer

| Authentication | Authorization    |
| -------------- | ---------------- |
| Who are you?   | What can you do? |
| Identity       | Permissions      |
| Login          | Access Control   |

---

## 37. What is JWT?

### Answer

JWT stands for JSON Web Token.

### Purpose

Stateless authentication.

---

## 38. Structure of JWT?

### Answer

```text
Header
Payload
Signature
```

---

## 39. Why Use JWT?

### Answer

Benefits:

* Stateless
* Fast
* Easy Scaling
* Cross-Service Authentication

---

## 40. What is OAuth?

### Answer

OAuth enables third-party authentication.

### Example

```text
Login with Google
Login with GitHub
```

---

## 41. What is Rate Limiting?

### Answer

Restricting request frequency.

### Example

```text
100 Requests / Minute
```

---

## 42. Why is Rate Limiting Important?

### Answer

Protects against:

* Abuse
* Bots
* DDoS Attacks
* Resource Exhaustion

---

## 43. How is Rate Limiting Implemented?

### Answer

Commonly using:

* Redis
* Token Bucket
* Leaky Bucket
* Sliding Window

---

## 44. What is a Message Queue?

### Answer

A queue used for asynchronous communication.

### Flow

```text
Producer
↓
Queue
↓
Consumer
```

---

## 45. Why Use Message Queues?

### Answer

Benefits:

* Decoupling
* Scalability
* Reliability
* Async Processing

---

## 46. What is RabbitMQ?

### Answer

RabbitMQ is a message broker implementing AMQP.

### Common Uses

* Background Tasks
* Job Queues
* Event Processing

---

## 47. What is Apache Kafka?

### Answer

Kafka is a distributed event streaming platform.

### Features

* High Throughput
* Scalability
* Durability

---

## 48. RabbitMQ vs Kafka?

### Answer

| RabbitMQ         | Kafka                |
| ---------------- | -------------------- |
| Message Queue    | Event Streaming      |
| Lower Throughput | Very High Throughput |
| Complex Routing  | Event Logs           |
| Task Processing  | Data Pipelines       |

---

## 49. What is Celery?

### Answer

Celery is a distributed task queue for Python.

### Common Uses

* Email Sending
* Data Processing
* Background Jobs
* Scheduled Tasks

---

## 50. How Does Celery Work?

### Answer

Flow:

```text
Application
↓
Celery Task
↓
Redis/RabbitMQ
↓
Worker
↓
Result
```

### Example

```python
from celery import Celery

app = Celery("tasks")

@app.task
def add(x, y):
    return x + y
```

---

## 51. What is FastAPI?

### Answer

FastAPI is a modern Python web framework for building high-performance APIs.

### Features

* Async Support
* Automatic Documentation
* Type Hints
* High Performance

---

## 52. Why is FastAPI Popular?

### Answer

Benefits:

* Very Fast
* Easy Development
* Built-in Validation
* OpenAPI Support

### Common Uses

* AI APIs
* LLM Applications
* Microservices
* ML Inference

---

## 53. FastAPI vs Flask?

### Answer

| FastAPI       | Flask        |
| ------------- | ------------ |
| Async Support | Mostly Sync  |
| Type Hints    | Optional     |
| Auto Docs     | Manual Setup |
| Faster        | Slower       |

---

## 54. FastAPI vs Django?

### Answer

| FastAPI        | Django             |
| -------------- | ------------------ |
| API Focused    | Full Framework     |
| Lightweight    | Heavyweight        |
| Async Friendly | Traditionally Sync |
| Microservices  | Monolith Friendly  |

---

## 55. What is ASGI?

### Answer

ASGI stands for:

```text
Asynchronous Server Gateway Interface
```

It is the modern replacement for WSGI.

---

## 56. What is WSGI?

### Answer

WSGI is a synchronous Python web server interface.

### Examples

* Flask
* Traditional Django

---

## 57. Why is ASGI Better for AI Applications?

### Answer

Benefits:

* Handles many concurrent requests
* Supports WebSockets
* Supports Async Operations

---

## 58. What is Uvicorn?

### Answer

Uvicorn is a high-performance ASGI server.

### Example

```bash
uvicorn main:app --reload
```

---

## 59. What is a Microservice?

### Answer

A Microservice is a small independently deployable service.

### Example

```text
User Service

Payment Service

Notification Service
```

---

## 60. Monolith vs Microservices?

### Answer

| Monolith           | Microservices      |
| ------------------ | ------------------ |
| Single Application | Multiple Services  |
| Easier Start       | Better Scaling     |
| Simpler Deployment | Complex Deployment |
| Tight Coupling     | Loose Coupling     |

---

## 61. What is an API Gateway?

### Answer

An API Gateway is the single entry point for services.

### Flow

```text
Client
↓
API Gateway
↓
Service A
Service B
Service C
```

---

## 62. Benefits of API Gateway?

### Answer

Benefits:

* Authentication
* Routing
* Rate Limiting
* Monitoring

---

## 63. What is Service Discovery?

### Answer

Service Discovery helps services find each other dynamically.

### Examples

* Consul
* Eureka
* Kubernetes DNS

---

## 64. Why is Service Discovery Needed?

### Answer

In distributed systems:

```text
Services constantly scale up/down
```

Static IP addresses become impractical.

---

## 65. What is Docker?

### Answer

Docker packages applications into lightweight containers.

### Benefits

* Portability
* Consistency
* Easy Deployment

---

## 66. Why Use Docker for Python Applications?

### Answer

Benefits:

* Same Environment Everywhere
* Dependency Isolation
* Faster Deployment

---

## 67. Example Dockerfile for FastAPI

### Example

```dockerfile
FROM python:3.12

WORKDIR /app

COPY . .

RUN pip install -r requirements.txt

CMD ["uvicorn","main:app","--host","0.0.0.0"]
```

---

## 68. What is Kubernetes?

### Answer

Kubernetes is a container orchestration platform.

### Responsibilities

* Scaling
* Deployment
* Monitoring
* Self-Healing

---

## 69. Why Use Kubernetes?

### Answer

Benefits:

* Auto Scaling
* Load Balancing
* Rolling Updates
* Fault Recovery

---

## 70. What is CI/CD?

### Answer

CI/CD stands for:

```text
Continuous Integration
Continuous Deployment
```

---

## 71. Popular CI/CD Tools?

### Answer

Examples:

* GitHub Actions
* Jenkins
* GitLab CI/CD
* Azure DevOps

---

## 72. What is Logging?

### Answer

Recording application events.

### Examples

```text
User Login

API Request

Database Error
```

---

## 73. What is Monitoring?

### Answer

Tracking system health and performance.

### Metrics

* CPU Usage
* Memory Usage
* Latency
* Error Rates

---

## 74. What is Observability?

### Answer

Observability helps understand internal system behavior.

### Pillars

```text
Logs
Metrics
Traces
```

---

## 75. Common Monitoring Tools?

### Answer

Examples:

* Prometheus
* Grafana
* ELK Stack
* OpenTelemetry
* Datadog

---

## 76. What is a Distributed System?

### Answer

A Distributed System consists of multiple computers working together as a single system.

### Examples

* Google Search
* Netflix
* Amazon
* Uber

---

## 77. Why Use Distributed Systems?

### Answer

Benefits:

* Scalability
* High Availability
* Fault Tolerance
* Performance

---

## 78. What is CAP Theorem?

### Answer

CAP Theorem states that a distributed system can guarantee only two of:

```text
Consistency
Availability
Partition Tolerance
```

---

## 79. What is Consistency?

### Answer

Every node sees the same data at the same time.

### Example

```text
User updates profile

All servers show updated profile immediately
```

---

## 80. What is Availability?

### Answer

Every request receives a response.

### Example

```text
Service remains operational
even during failures
```

---

## 81. What is Partition Tolerance?

### Answer

The system continues operating despite network failures.

### Example

```text
Server A loses connection
to Server B

System still works
```

---

## 82. What is Event-Driven Architecture?

### Answer

Services communicate through events.

### Flow

```text
Producer
↓
Event Bus
↓
Consumer
```

---

## 83. Benefits of Event-Driven Architecture?

### Answer

Benefits:

* Loose Coupling
* Scalability
* Reliability
* Asynchronous Processing

---

## 84. What is Eventual Consistency?

### Answer

Data becomes consistent over time.

### Example

```text
Database Replica
updates after a delay
```

---

## 85. Strong Consistency vs Eventual Consistency?

### Answer

| Strong Consistency | Eventual Consistency |
| ------------------ | -------------------- |
| Immediate Sync     | Delayed Sync         |
| Higher Accuracy    | Better Scalability   |
| Slower             | Faster               |

---

## 86. What is a Vector Database?

### Answer

A database optimized for vector embeddings.

### Examples

* Pinecone
* Weaviate
* Milvus
* ChromaDB

---

## 87. Why Are Vector Databases Important for AI?

### Answer

Used for:

* Semantic Search
* RAG Systems
* Similarity Search
* LLM Applications

---

## 88. What is an Embedding?

### Answer

An embedding is a numerical representation of data.

### Example

```text
"Cat"
↓

[0.23, 0.81, -0.14, ...]
```

---

## 89. What is RAG?

### Answer

RAG stands for:

```text
Retrieval Augmented Generation
```

---

## 90. RAG Architecture?

### Answer

Flow:

```text
User Question
↓
Embedding Model
↓
Vector Database
↓
Relevant Documents
↓
LLM
↓
Answer
```

---

## 91. Why Use RAG Instead of Fine-Tuning?

### Answer

Benefits:

* Cheaper
* Easier Updates
* No Retraining
* Better Knowledge Freshness

---

## 92. What is an AI Inference Service?

### Answer

A service that hosts ML/LLM models and generates predictions.

### Examples

```text
Fraud Detection

Recommendation Engine

ChatGPT-like API
```

---

## 93. Typical ML Serving Architecture?

### Answer

```text
User
↓
API Gateway
↓
FastAPI
↓
Model Service
↓
Redis Cache
↓
Database
```

---

## 94. What Challenges Exist in ML Serving?

### Answer

Common Challenges:

* Latency
* Throughput
* Model Versioning
* Monitoring
* Scalability

---

## 95. What is Model Versioning?

### Answer

Tracking multiple model versions.

### Example

```text
Fraud Model v1

Fraud Model v2

Fraud Model v3
```

---

## 96. What is Feature Store?

### Answer

A centralized repository for ML features.

### Benefits

* Reusability
* Consistency
* Faster Training

### Examples

* Feast
* Tecton

---

## 97. What is MLOps?

### Answer

MLOps applies DevOps principles to Machine Learning.

### Components

* CI/CD
* Monitoring
* Deployment
* Versioning

---

## 98. What Metrics Should Be Monitored in AI Systems?

### Answer

System Metrics:

* CPU
* Memory
* Latency

Model Metrics:

* Accuracy
* Precision
* Recall
* Drift

---

## 99. Design a ChatGPT-Like System

### Answer

Architecture:

```text
User
↓
Frontend
↓
API Gateway
↓
Authentication
↓
LLM Service
↓
Vector Database
↓
Redis Cache
↓
Monitoring
```

### Key Components

* FastAPI
* Redis
* PostgreSQL
* Vector DB
* OpenAI/LLM
* Kubernetes

---

## 100. What Python System Design Topics Are Most Important for AI Engineers?

### Answer

### Backend Fundamentals

* REST APIs
* FastAPI
* Authentication
* Caching
* Redis

### Scalability

* Load Balancers
* Horizontal Scaling
* Microservices
* Kubernetes

### Distributed Systems

* CAP Theorem
* Event-Driven Architecture
* Kafka
* RabbitMQ

### AI System Design

* RAG
* Vector Databases
* Embeddings
* Model Serving
* MLOps

### Production AI

* Monitoring
* Observability
* Model Versioning
* Feature Stores
* CI/CD

### Interview Focus Areas

For AI Engineer interviews (₹30–60+ LPA), the most frequently asked topics are:

```text
FastAPI
Redis
Kafka
Docker
Kubernetes
RAG
Vector Databases
MLOps
Model Serving
System Scalability
```


