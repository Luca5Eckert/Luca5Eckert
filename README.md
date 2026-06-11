# Lucas Eckert

Backend engineer building systems where **correctness under partial failure** and **explicit data ownership** are first-class concerns — not afterthoughts.

My work spans event-driven architecture, retrieval and recommendation infrastructure, and distributed systems designed to be observable and evolvable. I care less about framework familiarity and more about whether the system behaves correctly when things go wrong.

[Portfolio](https://lucas-eckert.vercel.app) · [LinkedIn](https://linkedin.com/in/lucas-ismael-eckert) · [Email](mailto:lucasismaeleckert@gmail.com)

---

## Currently

**At WEG** (CentroWEG / SENAI Industrial Apprenticeship Program)
Acting as Tech Lead Backend for **Portal Conecta** — service boundaries, OpenAPI contracts, RabbitMQ messaging, and explicit synchronous/asynchronous integration design.

**Personal**
Evolving VellumHub into v4 reliability hardening: transactional outbox, idempotent consumers, Flyway migrations, correlation ID propagation, and distributed-flow Testcontainers tests.
Maintaining Kairos v1 as a functional graph-augmented retrieval engine with passage-aware graph propagation, triple recall, and retrieval trace persistence.

---

## Projects

### [VellumHub](https://github.com/Luca5Eckert/VellumHub)

**The problem:** recommendation systems that query source-of-truth services at serving time create synchronous coupling — one slow or unavailable service degrades the entire recommendation path.

**The decision:** `recommendation-service` never calls catalog, user, or engagement services during the hot path. Catalog, user, and engagement changes propagate through Kafka and materialize into recommendation-owned read models: book embeddings, user profile vectors, and pre-joined metadata. The recommendation query path reads exclusively from local tables.

Key engineering decisions:
- Read model isolation through Event-Carried State Transfer
- Incremental user-profile learning from rating events classified as `DETRACTOR`, `NEUTRAL`, or `PROMOTER`
- Cold-start profile seeding from onboarding genre preferences — new users get ranked results immediately
- Retry-safe async processing with idempotent consumers, retry topics, and dead-letter topics
- Full local observability: Micrometer, Prometheus, Grafana, Loki, Tempo, OpenTelemetry, provisioned dashboards, alert rules, and runbooks
- v4 work: transactional outbox, schema migrations, correlation IDs, and distributed-flow testing

**The result:** personalized recommendation serving that is local (~80–120ms in-JVM vs ~300–500ms with a prior Python sidecar), fast, and resilient under partial failure of any source service.

`Java 21 · Spring Boot · Spring WebFlux · Kafka · PostgreSQL · pgvector · Redis · LangChain4j · Micrometer · Prometheus · Grafana · Loki · Tempo · OpenTelemetry · Testcontainers · Docker`

---

### [Kairos](https://github.com/Luca5Eckert/Kairos)

**The problem:** RAG systems that only do dense vector search lose structural relationships between concepts. A document about "machine learning" and one about "gradient descent" are semantically close, but the *relationship* between them carries information that flat retrieval discards.

**The decision:** dual-store architecture — PostgreSQL/pgvector for dense recall, Neo4j for structural reasoning and graph propagation. At ingestion, documents are split into passages, embedded locally with ONNX Runtime (`all-MiniLM-L6-v2`, 384-dim), and processed by Gemini/Spring AI to extract subject-predicate-object triples. Those triples become graph edges. Synonymy edges are also built at ingestion, so lexical variation becomes graph structure rather than a query-time problem.

Key engineering decisions:
- Personalized PageRank propagates over graph anchors to surface conceptually related passages that dense search would miss
- Dense recall, triple recall, and recognition filtering merged with Reciprocal Rank Fusion
- Per-user graph isolation treated as a first-class data-modeling concern — not a `WHERE` clause added as an afterthought
- Retrieval trace persistence for observability and future ranking improvements

**The result:** a retrieval engine that reasons over document structure, not just surface similarity.

`Java 21 · Spring Boot · Spring AI · ONNX Runtime · PostgreSQL · pgvector · Neo4j · Neo4j GDS · Gemini · Flyway · Docker`

---

### [OpenIT](https://github.com/Luca5Eckert/OpenIt)

**The problem:** IoT access control systems that release a gate based on optimistic UI state — before payment is confirmed in the backend — create a correctness gap between what the user sees and what the system has durably recorded.

**The decision:** gate release is gated on persisted backend payment confirmation, not frontend state. The full flow — ESP32 sensor → MQTT → Node-RED → Spring WebFlux backend → Mercado Pago webhook → MySQL — must complete and persist before any access is granted. Server-Sent Events push payment status to the React/TypeScript terminal without polling.

**The result:** a system where physical access is controlled by durable backend state. Payment, access control, persistence, and real-time update concerns are isolated into separate layers.

`Java 21 · Spring Boot · Spring WebFlux · MySQL · MQTT · ESP32 · Node-RED · Mercado Pago · React · TypeScript · Docker`

---

### [Vinculo](https://github.com/Luca5Eckert/vinculo)

Graph-based social network backend where relationships are modeled as first-class Neo4j edges rather than relational join tables. Connection requests have an explicit accepted/rejected lifecycle. Backend modules are separated across auth, person, connection, request, post, and graph concerns, with JWT-based authentication and role-based access control.

`Java 21 · Spring Boot · Neo4j · Spring Security · JWT · Testcontainers · Docker`

---

## Stack

**Languages**
Java · SQL · TypeScript · Python · JavaScript · C

**Backend**
Spring Boot · Spring WebFlux · Spring Security · Spring AI · REST APIs · JWT · SSE · JPA/Hibernate · JDBC · OpenAPI/Swagger

**Data & Storage**
PostgreSQL · pgvector · Neo4j · Neo4j GDS · Redis · MySQL

**Messaging & Integration**
Kafka · RabbitMQ · MQTT · Node-RED · Mercado Pago Checkout Pro

**Observability**
Spring Boot Actuator · Micrometer · Prometheus · Grafana · Loki · Tempo · Grafana Alloy · OpenTelemetry Java Agent

**AI & Retrieval**
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
Hexagonal Architecture · Clean Architecture · Domain-Driven Design · Bounded Contexts · CQRS · Ports and Adapters

**Retrieval & Recommendation**
RAG · Graph-Augmented Retrieval · Dense Passage Recall · Triple Recall · Personalized PageRank · Reciprocal Rank Fusion

**Backend Quality**
Integration Testing · Migration Safety · Observability · Distributed Tracing · Structured Logging · Rate Limiting · Failure-Safe Flows

---

## Certifications

- Confluent Certified Data Streaming Engineer — Foundations
- Confluent Apache Kafka Fundamentals Accreditation
- Neo4j Graph Data Science Certification
- Neo4j & Generative AI Certification
- Neo4j Fundamentals
- AWS Academy — Cloud Foundations
- AWS Academy — Generative AI Foundations

Coursework (WEG CentroWEG / SENAI): API Programming · Database Implementation · System Architecture · Cloud Computing · Information Security

---

## What I'm looking for

Backend or data-intensive systems roles — teams working on distributed systems, retrieval infrastructure, data pipelines, or applied ML/AI backends where correctness under partial failure is taken seriously and data modeling is a first-class concern.

Open to junior positions and internships where I can contribute to production-oriented backend codebases.
