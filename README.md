# Lucas Eckert

I like building backend systems where state has a clear path — from write models, through events and storage, to reliable application behavior.

**Junior Backend Developer** focused on Java/Spring, event-driven systems, distributed JVM services, and backend infrastructure for recommendations and retrieval.

[Portfolio](https://lucas-eckert.vercel.app) · [LinkedIn](https://linkedin.com/in/lucas-ismael-eckert) · [GitHub](https://github.com/Luca5Eckert) · [Email](mailto:lucasismaeleckert@gmail.com)

---

## Currently

Completing WEG's **CentroWEG / SENAI Industrial Apprenticeship Program** (3,200h) in Systems Development, with a path toward internal IT roles at WEG after completion.

- Leading backend architecture for **Portal Conecta**, a class-wide final project in early development — focused on Hub Core design, service boundaries, OpenAPI contracts, RabbitMQ-based messaging, and synchronous/asynchronous module integration.
- Evolving **VellumHub v3 → v4**: adding observability, idempotent consumers, transactional outbox, Flyway migrations, ops/security hardening, and Testcontainers-based distributed-flow tests.
- Refining **Kairos v1**: improving retrieval with HippoRAG 2.0-style passage-aware weighted PageRank, triple recall, recognition-memory filtering, failed-chunk reprocessing, and retrieval trace persistence.
- Studying distributed systems and derived data through *Designing Data-Intensive Applications* and applied Java/Spring work.

---

## Selected Systems

### [VellumHub](https://github.com/Luca5Eckert/VellumHub) · mature v3

Event-driven recommendation platform designed to serve personalized recommendations without query-time coupling to source-of-truth services.

The architecture centers on a WebFlux API Gateway, separate User/Catalog/Engagement/Recommendation services with service-owned PostgreSQL databases, Kafka-fed local read models, and a pgvector-enabled recommendation database. Recommendations are served from derived state — no synchronous upstream calls at query time.

v3 replaced earlier external ML-service coupling with JVM-native vector search and Kafka-fed read models. v4 focuses on production-grade distributed-systems concerns.

**Demonstrates**
- Event-Carried State Transfer over Kafka for local recommendation read models
- JVM-native semantic retrieval with LangChain4j 384-dimensional embeddings and HNSW indexing
- L2-normalized user and book vectors for calibrated cosine similarity
- Cold-start profile seeding from onboarding preferences
- Reactive API Gateway with Spring WebFlux, JWT validation, and Redis-backed rate limiting
- Kafka retry topics and Dead Letter Topics for resilient asynchronous processing

`Java 21 · Spring Boot · Spring WebFlux · Kafka · PostgreSQL · pgvector · Redis · LangChain4j · Docker`

---

### [Kairos](https://github.com/Luca5Eckert/Kairos) · operational v1

JVM-native graph-augmented retrieval engine that turns documents into a semantic memory graph.

Kairos persists source documents and chunks in PostgreSQL, generates local embeddings with ONNX Runtime, extracts factual subject-predicate-object triples through Spring AI/Gemini, stores semantic vectors in pgvector, and projects concepts, passages, and relationships into Neo4j. At query time, pgvector retrieves semantic anchors, Neo4j GDS Personalized PageRank expands through related concepts, and PostgreSQL rehydrates the final ranked chunks.

The goal is retrieval based on relationships between ideas, not only vector proximity.

**Demonstrates**
- Backend-first retrieval infrastructure — not notebook-based ML experimentation
- JVM-native embedding pipeline with ONNX Runtime
- Dual-store architecture with PostgreSQL/pgvector and Neo4j
- Graph-aware retrieval with Neo4j GDS Personalized PageRank
- LLM usage isolated to factual triple extraction behind a swappable domain port
- Hexagonal architecture separating domain, application, infrastructure, and presentation layers

`Java 21 · Spring Boot · Spring AI · ONNX Runtime · PostgreSQL · pgvector · Neo4j · Neo4j GDS · Gemini · Docker`

---

### [OpenIT](https://github.com/Luca5Eckert/OpenIt) · delivered CentroWEG project

Reactive IoT parking access-control system where backend-confirmed payment state controls physical access.

OpenIT coordinates ESP32 sensor events, MQTT communication, Node-RED orchestration, a Spring WebFlux backend, Mercado Pago Checkout Pro, MySQL persistence, and a React/TypeScript payment terminal. Delivered as a CentroWEG formative project — not a production deployment, but full end-to-end backend ownership over hardware events, payment state, persistence, real-time updates, and access-control rules.

**Demonstrates**
- MQTT hardware event handling from ESP32 devices
- Node-RED as an orchestration layer between IoT events and backend actions
- Server-Sent Events for payment status propagation without frontend polling
- Gate release tied to persisted payment confirmation, not optimistic UI state
- Clean Architecture / DDD-style separation between access and payment contexts

`Java 21 · Spring Boot · Spring WebFlux · MySQL · MQTT · ESP32 · Node-RED · Mercado Pago · React · TypeScript · Docker`

---

### [Vinculo](https://github.com/Luca5Eckert/vinculo)

Graph-based social network backend built around Neo4j relationships and modular backend architecture.

Models people, connection requests, accepted bidirectional relationships, posts, and network visualization endpoints. Uses Spring Boot, Neo4j, Spring Security, JWT, Docker, and a DDD/hexagonal module structure.

**Demonstrates**
- Neo4j-backed relationship modeling for social graph data
- Connection request lifecycle with accepted/rejected state transitions
- JWT authentication and role-based access control
- Modular backend structure across auth, person, connection, request, post, and graph modules

`Java 21 · Spring Boot · Neo4j · Spring Security · JWT · Docker · Testcontainers`

---

## Stack

**Languages** — Java · TypeScript · JavaScript · Python · SQL · C

**Backend** — Spring Boot · Spring WebFlux · Spring Security · REST APIs · JWT · SSE · JPA/Hibernate · JDBC · OpenAPI/Swagger

**Messaging** — Kafka · RabbitMQ · MQTT · Event-Carried State Transfer · Retry Topics · Dead Letter Topics

**Data** — PostgreSQL · pgvector · Neo4j · Neo4j GDS · Redis · MySQL

**AI & Retrieval** — Spring AI · LangChain4j · ONNX Runtime · Vector Search · RAG · Graph-Augmented Retrieval · Embeddings

**Architecture** — Hexagonal Architecture · DDD · Bounded Contexts · Clean Architecture · Distributed Systems · Eventual Consistency

**Testing** — JUnit 5 · Mockito · Testcontainers · JaCoCo

**Tooling** — Docker · Docker Compose · GitHub Actions · Maven · Git · Linux · Scrum

---

## Contact

[lucas-eckert.vercel.app](https://lucas-eckert.vercel.app) · [LinkedIn](https://linkedin.com/in/lucas-ismael-eckert) · [lucasismaeleckert@gmail.com](mailto:lucasismaeleckert@gmail.com)
