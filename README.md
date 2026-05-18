# Lucas Eckert

I like building backend systems where state has a clear path: from write models, through events and storage, to reliable application behavior.

**Junior Backend Developer** focused on **Java/Spring**, event-driven systems, distributed JVM services, and backend infrastructure for recommendations and retrieval.

[Portfolio](https://lucas-eckert.vercel.app) · [LinkedIn](https://linkedin.com/in/lucas-ismael-eckert) · [Email](mailto:lucasismaeleckert@gmail.com)

---

## currently

### WEG / CentroWEG-SENAI

- Completing WEG’s **CentroWEG / SENAI Industrial Apprenticeship Program** in Systems Development, a 3,200h internal formation path combining technical coursework with applied team projects.
- Working on formative software projects inside the program, with a path toward internal IT roles at WEG after completion.
- Leading backend architecture for **Portal Conecta**, a class-wide final project currently in early development, focused on Hub Core design, service boundaries, OpenAPI contracts, RabbitMQ-based messaging, and synchronous/asynchronous module integration.

### personal work

- Evolving **VellumHub v3 → v4**, a mature event-driven recommendation platform with Kafka, PostgreSQL/pgvector, Redis, LangChain4j, and Spring WebFlux. The next iteration focuses on observability, idempotent consumers, transactional outbox, Flyway migrations, ops/security hardening, and Testcontainers-based distributed-flow tests.
- Refining **Kairos v1**, an operational JVM-native graph-augmented retrieval engine with PostgreSQL/pgvector, Neo4j GDS, ONNX Runtime, Spring AI, and Gemini.
- Practicing algorithms and data structures in Java through a dedicated LeetCode/algorithms repository.

---

## what I build

- Backend services with explicit boundaries, persistence, APIs, and messaging
- Event-driven systems with Kafka, RabbitMQ, local read models, retries, and DLTs
- JVM-first applications using Java, Spring Boot, Spring WebFlux, PostgreSQL, Redis, and Docker
- Recommendation systems using events, user preferences, embeddings, and derived state
- Retrieval systems using vector search, knowledge graphs, graph traversal, and ranking
- Reactive APIs and real-time flows with SSE, MQTT, and non-blocking I/O

---

## selected systems

### [VellumHub](https://github.com/Luca5Eckert/VellumHub) · mature v3

Event-driven recommendation platform designed to serve personalized recommendations without query-time coupling to source-of-truth services.

VellumHub is organized around a WebFlux API Gateway, separate User/Catalog/Engagement/Recommendation services, service-owned PostgreSQL databases, Redis-backed gateway rate limiting, Kafka messaging, and a pgvector-enabled recommendation database. Recommendation queries are served from local derived state instead of synchronously calling upstream services at runtime.

The current v3 architecture replaced earlier external ML-service coupling with JVM-native vector search and Kafka-fed read models. The v4 direction focuses on distributed-systems production concerns: observability, idempotent consumers, transactional outbox, Flyway migrations, ops/security hardening, and Testcontainers-based integration tests.

**What it proves**

- Event-Carried State Transfer over Kafka for local recommendation read models
- Query-time recommendation serving without synchronous upstream service calls
- JVM-native semantic retrieval with LangChain4j 384-dimensional embeddings
- PostgreSQL/pgvector-backed candidate retrieval with HNSW indexing
- L2-normalized user and book vectors for calibrated cosine similarity
- Cold-start profile seeding from onboarding preferences
- Reactive API Gateway with Spring WebFlux, JWT validation, and Redis-backed rate limiting
- Kafka retry topics and Dead Letter Topics for resilient asynchronous processing
- Architecture evolution from external ML calls to local vector search and derived event state

**Stack**

`Java 21 · Spring Boot · Spring WebFlux · Kafka · PostgreSQL · pgvector · Redis · LangChain4j · Docker`

---

### [Kairos](https://github.com/Luca5Eckert/Kairos) · operational v1

JVM-native graph-augmented retrieval engine that turns documents into a semantic memory graph.

Kairos persists source documents and chunks in PostgreSQL, generates local embeddings with ONNX Runtime, extracts factual subject-predicate-object triples through Spring AI/Gemini, stores semantic vectors in pgvector, and projects concepts, passages, and relationships into Neo4j.

At query time, pgvector retrieves semantic anchors, Neo4j GDS Personalized PageRank expands through related concepts and passages, and PostgreSQL rehydrates the final ranked chunks. The goal is retrieval based on relationships between ideas, not only vector proximity.

Current work focuses on HippoRAG 2.0-style retrieval improvements, including passage-aware weighted PageRank, triple recall, recognition-memory filtering, failed-chunk reprocessing, and retrieval trace persistence.

**What it proves**

- Backend-first retrieval infrastructure, not notebook-based ML experimentation
- Durable ingestion before embedding and graph indexing
- JVM-native embedding pipeline with ONNX Runtime
- Dual-store architecture with PostgreSQL/pgvector and Neo4j
- Semantic anchor search with pgvector
- Graph-aware retrieval with Neo4j GDS Personalized PageRank
- LLM usage isolated to factual triple extraction behind a swappable domain port
- Hexagonal architecture separating domain, application, infrastructure, and presentation layers
- Operational local pipeline with Docker Compose, health checks, auth endpoints, ingestion, enrichment, and retrieval

**Stack**

`Java 21 · Spring Boot · Spring AI · ONNX Runtime · PostgreSQL · pgvector · Neo4j · Neo4j GDS · Gemini · Docker`

---

### [OpenIT](https://github.com/Luca5Eckert/OpenIt) · delivered CentroWEG project

Reactive IoT parking access-control system where backend-confirmed payment state controls physical access.

OpenIT coordinates ESP32 sensor events, MQTT communication, Node-RED orchestration, a Spring WebFlux backend, Mercado Pago Checkout Pro, MySQL persistence, and a React/TypeScript payment terminal. The system models a complete flow from vehicle entry to payment confirmation and gate release.

The project was delivered as a CentroWEG formative project. It was not a production deployment, but it demonstrates end-to-end backend ownership over hardware events, payment state, persistence, real-time updates, and access-control rules.

**What it proves**

- MQTT hardware event handling from ESP32 devices
- Node-RED as an orchestration layer between IoT events and backend actions
- Spring WebFlux backend for real-time payment/access-state flows
- Server-Sent Events for payment status propagation without frontend polling
- Mercado Pago Checkout Pro integration with webhook-confirmed payment state
- Gate release tied to persisted payment confirmation, not optimistic UI state
- MySQL-backed access and payment persistence
- Clean Architecture / DDD-style separation between access and payment contexts
- Frontend terminal built with React and TypeScript

**Stack**

`Java 21 · Spring Boot · Spring WebFlux · MySQL · MQTT · ESP32 · Node-RED · Mercado Pago · React · TypeScript · Docker`

---

### [Vinculo](https://github.com/Luca5Eckert/vinculo)

Graph-based social network backend built around Neo4j relationships and modular backend architecture.

Vinculo models people, connection requests, accepted bidirectional relationships, posts, and network visualization endpoints. It uses Spring Boot, Neo4j, Spring Security, JWT, Docker, and a DDD/hexagonal module structure.

**What it proves**

- Neo4j-backed relationship modeling for social graph data
- Connection request lifecycle with accepted/rejected state transitions
- Bidirectional relationship creation after accepted requests
- JWT authentication and role-based access control
- Modular backend structure across auth, person, connection, request, post, and graph modules
- OpenAPI/Swagger documentation and Docker-based local execution

**Stack**

`Java 21 · Spring Boot · Neo4j · Spring Security · JWT · Docker · Testcontainers`

---

## stack

**Languages**  
Java · TypeScript · JavaScript · Python · SQL · C

**Backend**  
Spring Boot · Spring WebFlux · Spring Security · REST APIs · JWT · SSE · JPA/Hibernate · JDBC · OpenAPI/Swagger

**Messaging and event-driven systems**  
Kafka · RabbitMQ · MQTT · Event-Carried State Transfer · Retry Topics · Dead Letter Topics · Event-Driven Read Models

**Data stores**  
PostgreSQL · pgvector · Neo4j · Neo4j GDS · Redis · MySQL

**AI, retrieval, and recommendation systems**  
Spring AI · LangChain4j · ONNX Runtime · Vector Search · RAG · Graph-Augmented Retrieval · Recommendation Systems · Embeddings

**Architecture and testing**  
Service Boundaries · Distributed Systems · Hexagonal Architecture · DDD · Bounded Contexts · Clean Architecture · Eventual Consistency · JUnit 5 · Mockito · Testcontainers · JaCoCo

**Platform and tooling**  
Docker · Docker Compose · GitHub Actions · Maven · Git · Linux · GitHub Projects · Scrum

---

## learning

Currently focusing on:

- Distributed systems and derived data
- Event-driven backend architecture
- Recommendation and retrieval infrastructure
- Vector search and graph-based retrieval
- ML fundamentals for backend-integrated systems

Main references:

- Designing Data-Intensive Applications
- Neural Networks and Deep Learning

---

## contact

- Portfolio: [lucas-eckert.vercel.app](https://lucas-eckert.vercel.app)
- LinkedIn: [linkedin.com/in/lucas-ismael-eckert](https://linkedin.com/in/lucas-ismael-eckert)
- GitHub: [github.com/Luca5Eckert](https://github.com/Luca5Eckert)
- Email: [lucasismaeleckert@gmail.com](mailto:lucasismaeleckert@gmail.com)
