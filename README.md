# Lucas Eckert

Junior Backend Developer focused on Java/Spring, distributed JVM services, event-driven architecture, and backend systems that turn data, events, and ML signals into reliable application behavior.

My main focus is backend engineering: service boundaries, APIs, messaging, persistence, asynchronous processing, and resilient application design. Some of my projects also explore recommendation systems, vector search, and graph-augmented retrieval using PostgreSQL/pgvector, Neo4j, ONNX Runtime, and Spring AI.

[Portfolio](https://lucas-eckert.vercel.app) · [LinkedIn](https://linkedin.com/in/lucas-ismael-eckert) · [Email](mailto:lucasismaeleckert@gmail.com)

---

## currently

- Backend developer in WEG/CentroWEG-SENAI’s 3,200h Industrial Apprenticeship Program.
- Leading backend architecture for **Portal Conecta**, a class-wide final project currently in early development, focused on service boundaries, Hub Core design, OpenAPI contracts, RabbitMQ-based messaging, and synchronous/asynchronous communication between modules.
- Evolving **VellumHub v3 → v4**, a mature event-driven recommendation platform with Kafka, PostgreSQL/pgvector, Redis, LangChain4j, and Spring WebFlux. The next iteration focuses on distributed-systems production concerns such as observability, idempotent consumers, transactional outbox, Flyway migrations, ops/security hardening, and Testcontainers-based integration tests.
- Refining **Kairos v1**, an operational JVM-native graph-augmented retrieval engine with PostgreSQL/pgvector, Neo4j GDS, ONNX Runtime, Spring AI, and Gemini. Current work focuses on HippoRAG 2.0-style retrieval improvements, including passage-aware weighted PageRank, triple recall, recognition-memory filtering, failed-chunk reprocessing, and retrieval trace persistence.
- Studying distributed systems, derived data, backend architecture, recommendation systems, and retrieval infrastructure.

---

## what I build

- Backend services with clear boundaries, persistence, APIs, and messaging
- Event-driven systems with Kafka, RabbitMQ, local read models, and resilient consumers
- JVM-first applications using Java, Spring Boot, Spring WebFlux, PostgreSQL, Redis, and Docker
- Recommendation systems using events, user preferences, embeddings, and derived state
- Retrieval systems using vector search, knowledge graphs, graph traversal, and ranking
- Reactive APIs and real-time flows with SSE, MQTT, and non-blocking I/O

---

## selected systems

### [VellumHub](https://github.com/Luca5Eckert/VellumHub) · mature v3

Event-driven recommendation platform currently at v3, evolving toward v4 with a focus on observability, idempotent consumers, transactional outbox, schema migrations, operational security, and integration testing for distributed flows.

VellumHub uses Kafka events to build local read models across catalog, engagement, user, and recommendation boundaries. Recommendation queries are served from derived state instead of synchronously calling upstream services at runtime.

**What it proves**

- Event-Carried State Transfer over Kafka for local recommendation read models
- Query-time recommendation serving without synchronous upstream service calls
- JVM-native semantic retrieval with PostgreSQL/pgvector and 384-dimensional embeddings
- Cold-start profile seeding from onboarding preferences
- Reactive API Gateway with Spring WebFlux, JWT validation, and Redis-backed rate limiting
- Retry topics and Dead Letter Topics for resilient asynchronous processing
- Architecture evolution from external ML calls to JVM-native vector search and resilient event-driven state

**Stack**

`Java 21 · Spring Boot · Spring WebFlux · Kafka · PostgreSQL · pgvector · Redis · LangChain4j · Docker`

---

### [Kairos](https://github.com/Luca5Eckert/Kairos) · operational v1

JVM-native graph-augmented retrieval engine that turns documents into a semantic memory graph.

Kairos combines durable PostgreSQL storage, pgvector semantic anchors, local ONNX embeddings, Spring AI/Gemini triple extraction, and Neo4j GDS Personalized PageRank to retrieve context connected by meaning and relationships — not only vector similarity.

The v1 pipeline is operational: source ingestion, durable chunking, local embeddings, triple extraction, pgvector semantic search, Neo4j graph construction, graph expansion, and PostgreSQL rehydration are already implemented. Current work focuses on HippoRAG 2.0-style retrieval improvements, including passage-aware weighted PageRank, triple recall, recognition-memory filtering, failed-chunk reprocessing, and retrieval trace persistence.

**What it proves**

- Backend-first retrieval infrastructure, not notebook-based ML experimentation
- JVM-native embedding pipeline with ONNX Runtime
- Dual-store architecture with PostgreSQL/pgvector and Neo4j
- Semantic anchor search with pgvector
- Graph-aware retrieval with Neo4j GDS Personalized PageRank
- LLM usage isolated to factual triple extraction through a swappable domain port
- Hexagonal architecture separating domain, application, infrastructure, and presentation layers
- Operational local pipeline with Docker Compose, health checks, auth endpoints, ingestion, enrichment, and retrieval

**Stack**

`Java 21 · Spring Boot · Spring AI · ONNX Runtime · PostgreSQL · pgvector · Neo4j · Neo4j GDS · Gemini · Docker`

---

### [OpenIT](https://github.com/Luca5Eckert/OpenIt) · delivered

Reactive IoT parking access-control system where backend-confirmed payment state controls physical access.

OpenIT bridges MQTT events from ESP32 hardware with a Spring WebFlux backend, allowing access state to be updated in real time without polling. The system integrates payment flow with physical access grants and exposes live state updates to the frontend.

**What it proves**

- MQTT hardware event handling from ESP32 devices
- Reactive backend with Spring WebFlux
- Real-time access-state propagation with Server-Sent Events
- Payment flow tied to physical access control
- Backend ownership in an applied team project
- Integration between hardware events, payment state, and application state

**Stack**

`Java 21 · Spring Boot · Spring WebFlux · MySQL · MQTT · ESP32 · Node-RED · Mercado Pago · React · TypeScript`

---

## engineering focus

- Java/Spring backend development
- Distributed JVM services
- Event-driven architecture
- Service boundaries and backend modularity
- Asynchronous messaging with Kafka, RabbitMQ, and MQTT
- Event-built read models and derived data
- PostgreSQL, Redis, Neo4j, and pgvector-backed systems
- Recommendation systems and cold-start strategies
- Graph-augmented retrieval and semantic memory systems
- Observability, idempotency, outbox, migrations, and integration testing for distributed flows
- Reactive APIs with Spring WebFlux
- API gateways, rate limiting, retries, and Dead Letter Topics
- Domain-driven design and hexagonal architecture

---

## stack

**Languages**  
Java · TypeScript · JavaScript · Python · SQL · C

**Backend**  
Spring Boot · Spring WebFlux · Spring Security · REST APIs · JWT · SSE · JPA/Hibernate · JDBC · OpenAPI/Swagger

**Messaging and event-driven systems**  
Kafka · RabbitMQ · MQTT · Event-Carried State Transfer · Retry Topics · Dead Letter Topics · Event-Driven Read Models

**Data stores**  
PostgreSQL · pgvector · Neo4j · Redis · MySQL

**AI, retrieval, and recommendation systems**  
Spring AI · LangChain4j · ONNX Runtime · Neo4j GDS · Vector Search · RAG · Graph-Augmented Retrieval · Recommendation Systems · Embeddings

**Architecture**  
Service Boundaries · Distributed Systems · Hexagonal Architecture · DDD · Bounded Contexts · Clean Architecture · Eventual Consistency

**Testing**  
JUnit 5 · Mockito · Testcontainers · Spring Boot Test · JaCoCo

**Platform and tooling**  
Docker · Docker Compose · GitHub Actions · Maven · Git · Linux · GitHub Projects · Scrum

---

## learning

Currently deepening my understanding of:

- Distributed systems and derived data
- Replication, consistency, and event-driven data flows
- Backend architecture with Java/Spring
- Recommendation systems and retrieval infrastructure
- Vector databases and graph-based retrieval
- ML fundamentals for backend-integrated systems

Main references include:

- Designing Data-Intensive Applications
- Neural Networks and Deep Learning
- Practical backend architecture through applied Java/Spring projects

---

## contact

- Portfolio: [lucas-eckert.vercel.app](https://lucas-eckert.vercel.app)
- LinkedIn: [linkedin.com/in/lucas-ismael-eckert](https://linkedin.com/in/lucas-ismael-eckert)
- GitHub: [github.com/Luca5Eckert](https://github.com/Luca5Eckert)
- Email: [lucasismaeleckert@gmail.com](mailto:lucasismaeleckert@gmail.com)
