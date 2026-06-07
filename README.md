# Lucas Eckert

Backend developer focused on data-intensive backend systems, event-driven architecture, and retrieval infrastructure.

I build backend systems where correctness under partial failure, derived data, retrieval quality, operational visibility, and long-term evolvability are first-class concerns. My work spans recommendation pipelines, graph-augmented retrieval engines, and IoT/payment systems — tied together by explicit state, durable data ownership, and observable behavior.

[Portfolio](https://lucas-eckert.vercel.app) · [LinkedIn](https://linkedin.com/in/lucas-ismael-eckert) · [Email](mailto:lucasismaeleckert@gmail.com)

---

## Currently

Completing WEG's **CentroWEG / SENAI Industrial Apprenticeship Program** in Systems Development.

**At WEG:**

- Acting as **Tech Lead Backend** for **Portal Conecta**, focused on service boundaries, OpenAPI contracts, RabbitMQ messaging, and explicit synchronous/asynchronous integration.

**Personal projects:**

- Evolving **VellumHub v4** with transactional outbox, idempotent consumers, Flyway migrations, correlation ID propagation, Micrometer/Prometheus metrics, Grafana dashboards, Loki logs, Tempo traces, alert rules, runbooks, and Testcontainers-based distributed-flow tests.
- Maintaining **Kairos v1** as a functional graph-augmented retrieval engine, with passage-aware graph propagation, triple recall, recognition filtering, per-user graph isolation, and retrieval trace persistence.

Studying distributed systems and derived data through *Designing Data-Intensive Applications* and applied Java/Spring work.

---

## Technical Focus

- Java/Spring backend systems
- Event-driven and data-intensive applications
- Retrieval and recommendation infrastructure
- Explicit data ownership, derived state, and local read models
- Backend reliability, observability, testing, and maintainability

---

## Selected Systems

### [VellumHub](https://github.com/Luca5Eckert/VellumHub) · mature v3 · v4 in progress

**Recommendations without synchronous coupling.**

Event-driven book recommendation platform implemented as five JVM services: gateway, user, catalog, engagement, and recommendation.

The core architectural decision is that `recommendation-service` does not call source-of-truth services during the recommendation hot path. Instead, catalog, user, and engagement changes are propagated through Kafka and materialized into recommendation-owned read models: book embeddings, user profile vectors, and pre-joined metadata.

This keeps personalized recommendation serving local, fast, and resilient under partial failure.

**Key engineering decisions**

- Read model isolation through Event-Carried State Transfer.
- Recommendation-owned derived state instead of query-time service coupling.
- pgvector similarity search over 384-dimensional embeddings.
- Incremental user-profile learning from rating events classified as `DETRACTOR`, `NEUTRAL`, or `PROMOTER`.
- Cold-start profile seeding from onboarding genre preferences.
- Retry-safe asynchronous processing with idempotent consumers, retry topics, and dead-letter topics.
- Local observability stack with Spring Boot Actuator, Micrometer, Prometheus, Grafana, Loki, Tempo, Grafana Alloy, and OpenTelemetry Java Agent.
- Custom Kafka, DLT, and business metrics with low-cardinality labels, provisioned dashboards, Prometheus alert rules, and operational runbooks.
- v4 work around transactional outbox, schema migrations, correlation IDs, observability hardening, and distributed-flow testing.

`Java 21 · Spring Boot · Spring WebFlux · Kafka · PostgreSQL · pgvector · Redis · LangChain4j · Micrometer · Prometheus · Grafana · Loki · Tempo · OpenTelemetry · Docker · Testcontainers`

---

### [Kairos](https://github.com/Luca5Eckert/Kairos) · functional v1

**Documents as a self-building semantic memory graph.**

JVM-native graph-augmented retrieval backend that turns documents into a semantic memory graph.

Kairos combines dense vector search with graph traversal. PostgreSQL/pgvector stores embeddings for dense recall; Neo4j stores passages, concepts, triples, synonymy relations, and semantic graph structure. The system is designed as retrieval infrastructure, not as a chatbot wrapper.

**Key engineering decisions**

- Dual-store retrieval architecture: pgvector for dense search, Neo4j for structural reasoning and graph propagation.
- Local embedding generation with ONNX Runtime using `all-MiniLM-L6-v2` 384-dimensional embeddings.
- Gemini/Spring AI integration for structured subject-predicate-object triple extraction.
- Personalized PageRank over graph anchors for concept propagation.
- Dense passage recall, triple recall, recognition filtering, and Reciprocal Rank Fusion.
- Ingestion-time synonymy edges, so lexical variation becomes graph structure instead of query-time fuzzy matching.
- Per-user graph isolation treated as a first-class data-modeling concern.
- Retrieval trace persistence for observability and future ranking improvements.

`Java 21 · Spring Boot · Spring AI · ONNX Runtime · PostgreSQL · pgvector · Neo4j · Neo4j GDS · Gemini · Flyway · Docker`

---

### [OpenIT](https://github.com/Luca5Eckert/OpenIt) · delivered

**Physical access controlled by durable backend state.**

Reactive IoT parking access-control system where backend-confirmed payment state controls physical access.

OpenIT integrates ESP32 sensors, MQTT, Node-RED orchestration, a Spring WebFlux backend, Mercado Pago Checkout Pro, MySQL persistence, and a React/TypeScript payment terminal. The project covers the full flow from physical sensor events to payment confirmation and gate release.

**Key engineering decisions**

- Gate release is tied to persisted backend payment confirmation, not optimistic UI state.
- ESP32 sensor events are propagated through MQTT and Node-RED.
- Webhook-based payment confirmation is persisted in MySQL.
- Server-Sent Events update the frontend payment status without polling.
- Hardware orchestration is separated from backend business rules.
- Payment, access control, persistence, and real-time update concerns are isolated.

`Java 21 · Spring Boot · Spring WebFlux · MySQL · MQTT · ESP32 · Node-RED · Mercado Pago · React · TypeScript · Docker`

---

### [Vinculo](https://github.com/Luca5Eckert/vinculo)

**Social relationships modeled as a graph.**

Graph-based social network backend built around Neo4j relationships and modular backend architecture.

It models people, connection requests, accepted bidirectional relationships, posts, and network visualization endpoints.

**Key engineering decisions**

- Neo4j is used for relationship-first social graph modeling.
- Connection requests have an explicit lifecycle with accepted/rejected transitions.
- Authentication and authorization are handled through JWT and role-based access control.
- Backend modules are separated across auth, person, connection, request, post, and graph concerns.

`Java 21 · Spring Boot · Neo4j · Spring Security · JWT · Docker · Testcontainers`

---

## Technologies

**Languages**  
Java · SQL · TypeScript · Python · JavaScript · C

**Backend**  
Spring Boot · Spring WebFlux · Spring Security · Spring AI · REST APIs · JWT · SSE · JPA/Hibernate · JDBC · OpenAPI/Swagger

**Data & Storage**  
PostgreSQL · pgvector · Neo4j · Neo4j GDS · Redis · MySQL

**Messaging & Integration**  
Kafka · RabbitMQ · MQTT · Node-RED · Mercado Pago Checkout Pro

**Observability**  
Spring Boot Actuator · Micrometer · Prometheus · Grafana · Loki · Tempo · Grafana Alloy · OpenTelemetry Java Agent · structured JSON logs · alert rules · runbooks

**AI & Retrieval Tooling**  
LangChain4j · ONNX Runtime · Gemini

**Infrastructure & Quality**  
Docker · Flyway · GitHub Actions · Maven · Git · Linux · JUnit 5 · Mockito · Testcontainers · JaCoCo

---

## Engineering Concepts

**Event-Driven Systems**  
Event-Carried State Transfer · Transactional Outbox · Idempotent Consumers · Retry Topics · Dead Letter Topics · Correlation ID Propagation · Eventual Consistency · Partial Failure Handling

**Data Modeling & State Ownership**  
Service-Owned Persistence · Write/Read Model Separation · Derived Data · Local Read Models · Schema Evolution · Data Ownership Boundaries

**Architecture**  
Hexagonal Architecture · Clean Architecture · Domain-Driven Design · Bounded Contexts · CQRS · Service Boundaries · Ports and Adapters

**Retrieval & Recommendation**  
RAG · Graph-Augmented Retrieval · Semantic Search · Dense Passage Recall · Triple Recall · Personalized PageRank · Reciprocal Rank Fusion · Recommendation Reranking

**Backend Quality**  
Automated Testing · Integration Testing · Migration Safety · Observability · Metrics · Distributed Tracing · Structured Logging · Rate Limiting · Failure-Safe Flows

---

## Certifications & Coursework

Certifications, accreditations, and training badges:

- Confluent Certified Data Streaming Engineer — Foundations
- Confluent Apache Kafka Fundamentals Accreditation
- Neo4j Graph Data Science Certification
- Neo4j & Generative AI Certification
- Neo4j Fundamentals
- AWS Academy Graduate — Cloud Foundations
- AWS Academy Graduate — Generative AI Foundations

Relevant coursework at WEG CentroWEG / SENAI: API Programming, Database Implementation, System Architecture, Cloud Computing, and Information Security.

---

## What I'm looking for

Backend or data-intensive systems engineering roles — ideally in teams working on distributed systems, retrieval infrastructure, data pipelines, or applied ML/AI backends.

I am interested in environments where correctness under partial failure is taken seriously, data modeling is a first-class concern, and backend systems are designed to evolve over time.

Open to junior positions and internships where I can contribute to backend codebases and grow through production-oriented engineering work.

[Portfolio](https://lucas-eckert.vercel.app) · [LinkedIn](https://linkedin.com/in/lucas-ismael-eckert) · [Email](mailto:lucasismaeleckert@gmail.com)
