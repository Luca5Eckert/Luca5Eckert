# Lucas Eckert

I build backend systems where things still work correctly when parts of the infrastructure go down.

**Correctness under partial failure** and **explicit data ownership** are design constraints, not afterthoughts. My work spans event-driven architecture, retrieval and recommendation infrastructure, and distributed systems built to be observable and evolvable.

[Portfolio](https://lucas-eckert.vercel.app) · [LinkedIn](https://linkedin.com/in/lucas-ismael-eckert) · [Email](mailto:lucasismaeleckert@gmail.com)

---

## Currently

**At WEG** — CentroWEG / SENAI Industrial Apprenticeship Program
Acting as tech lead backend on **Portal Conecta**: service boundaries, OpenAPI contracts, RabbitMQ messaging, explicit synchronous/asynchronous integration design.

**Personal**
Hardening VellumHub v4: transactional outbox, idempotent consumers, Flyway migrations, correlation ID propagation, distributed-flow Testcontainers tests.
Maintaining Kairos as a functional graph-augmented retrieval engine with passage-aware graph propagation, triple recall, and retrieval trace persistence.

---

## Projects

### [VellumHub](https://github.com/Luca5Eckert/VellumHub) — event-driven book recommendation

**Problem:** recommendation systems that query source-of-truth services at serving time create synchronous coupling. One slow or unavailable service degrades the entire recommendation path.

**Decision:** `recommendation-service` never calls catalog, user, or engagement services during the hot path. Changes propagate through Kafka and materialize into recommendation-owned read models: book embeddings, user profile vectors, pre-joined metadata. The query path reads exclusively from local tables.

**Notable decisions:**
- Read model isolation through Event-Carried State Transfer
- Incremental user-profile updates from rating events classified as `DETRACTOR`, `NEUTRAL`, or `PROMOTER`
- Cold-start seeding from onboarding genre preferences — new users get ranked results immediately
- Retry-safe async processing: idempotent consumers, retry topics, dead-letter topics
- Full local observability stack: Micrometer, Prometheus, Grafana, Loki, Tempo, OpenTelemetry, provisioned dashboards, alert rules, runbooks

**Result:** personalized serving that stays available under partial failure of any source service — ~80–120ms in-JVM vs ~300–500ms with a prior Python sidecar.

`Java 21 · Spring Boot · Spring WebFlux · Kafka · PostgreSQL · pgvector · Redis · LangChain4j · Micrometer · Prometheus · Grafana · Loki · Tempo · OpenTelemetry · Testcontainers · Docker`

---

### [Kairos](https://github.com/Luca5Eckert/Kairos) — graph-augmented retrieval engine

**Problem:** RAG systems that rely only on dense vector search lose structural relationships between concepts. A passage about "machine learning" and one about "gradient descent" are close in embedding space — but the *relationship* between them carries information that flat retrieval discards.

**Decision:** dual-store architecture, with each store doing what it's actually good at.

- **PostgreSQL + pgvector** is the source of truth for durable text and semantic similarity. Passage embeddings and triple embeddings live here; dense recall runs against HNSW indexes.
- **Neo4j + Graph Data Science** stores the structural projection — `Passage` nodes, `PhraseNode` concepts, `CONTAINS` and `TRIPLE` edges. Graph propagation runs here via Personalized PageRank.

Neither store substitutes for the other. Postgres answers "what is semantically close to this query?" Neo4j answers "what else does the graph connect to these anchors?" The retrieval path merges both signals.

At ingestion, documents are split into passages, embedded locally via ONNX Runtime (`all-MiniLM-L6-v2`, 384-dim), and processed by Gemini/Spring AI to extract subject-predicate-object triples. Triples become graph edges persisted in both stores. The embedding model runs fully in-process on the JVM — no Python sidecar.

**Notable decisions:**
- Personalized PageRank propagates over graph anchors to surface conceptually related passages that dense search alone would miss
- Dense recall, triple recall, and recognition-memory filtering merged with Reciprocal Rank Fusion
- Per-user graph isolation as a first-class data-modeling decision — not a `WHERE` clause bolted on afterward
- Retrieval trace persistence for observability and future ranking improvements

**Result:** a retrieval engine that reasons over document structure, not just surface similarity. 183 tests passing, 69% line coverage.

`Java 21 · Spring Boot · Spring AI · ONNX Runtime · PostgreSQL · pgvector · Neo4j · Neo4j GDS · Gemini · Flyway · Docker`

---

### [OpenIT](https://github.com/Luca5Eckert/OpenIt) — IoT access control

**Problem:** IoT payment flows that release a gate based on optimistic UI state — before backend confirmation — create a correctness gap between what the user sees and what the system has durably recorded.

**Decision:** gate release is gated on persisted backend payment confirmation. The full flow (ESP32 → MQTT → Node-RED → Spring WebFlux → Mercado Pago webhook → MySQL) must complete and persist before access is granted. Server-Sent Events push payment status to the React/TypeScript terminal without polling.

`Java 21 · Spring Boot · Spring WebFlux · MySQL · MQTT · ESP32 · Node-RED · Mercado Pago · React · TypeScript · Docker`

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
Integration Testing · Migration Safety · Observability · Distributed Tracing · Structured Logging · Failure-Safe Flows

---

## Certifications

- Confluent Certified Data Streaming Engineer — Foundations
- Confluent Apache Kafka Fundamentals Accreditation
- Neo4j Graph Data Science Certification
- Neo4j & Generative AI Certification
- Neo4j Fundamentals
- AWS Academy — Cloud Foundations
- AWS Academy — Generative AI Foundations

Coursework (CentroWEG / SENAI): API Programming · Database Implementation · System Architecture · Cloud Computing · Information Security

---

## What I'm looking for

Backend or data-intensive systems roles — distributed systems, retrieval infrastructure, data pipelines, applied ML/AI backends. Teams where correctness under partial failure is taken seriously and data modeling is a first-class concern.

Open to junior positions and internships.
