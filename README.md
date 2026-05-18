# Lucas Eckert

I like building backend systems where state has a clear path — from write models, through events and storage, to reliable application behavior.

**Junior Backend Developer** focused on Java/Spring, event-driven systems, distributed JVM services, and backend infrastructure for recommendations and retrieval.

[Portfolio](https://lucas-eckert.vercel.app) · [LinkedIn](https://linkedin.com/in/lucas-ismael-eckert) · [GitHub](https://github.com/Luca5Eckert) · [Email](mailto:lucasismaeleckert@gmail.com)

---

## Currently

Completing WEG's **CentroWEG / SENAI Industrial Apprenticeship Program** (3,200h) in Systems Development, with a path toward internal IT roles at WEG after completion.

- Leading backend architecture for **Portal Conecta**, a class-wide final project in early development — focused on Hub Core design, service boundaries, OpenAPI contracts, RabbitMQ-based messaging, and synchronous/asynchronous module integration.
- Evolving **VellumHub v3 → v4**: adding observability, idempotent consumers, transactional outbox, Flyway migrations, ops/security hardening, and Testcontainers-based distributed-flow tests.
- Refining **Kairos v1**: rebuilding retrieval toward HippoRAG 2.0 — passage-aware weighted PageRank, recognition memory filtering, triple recall, and retrieval trace persistence.
- Studying distributed systems and derived data through *Designing Data-Intensive Applications* and applied Java/Spring work.

---

## Selected Systems

### [VellumHub](https://github.com/Luca5Eckert/VellumHub) · mature v3

Event-driven recommendation platform designed to serve personalized recommendations without query-time coupling to source-of-truth services.

Five microservices — gateway, user, catalog, engagement, recommendation — each owning its domain and its database. The central architectural decision is that recommendation-service never calls catalog-service at query time. Instead, it maintains local read models fed by Kafka events: book embeddings, user profile vectors, and pre-joined metadata for low-latency responses.

Recommendations are served from a CTE query over pgvector: ANN search via HNSW over 384-dimensional L2-normalized embeddings generates 200 candidates, reranked with a 70/30 blend of vector distance and popularity score. User profiles are updated incrementally on rating events — each rating is classified as DETRACTOR, NEUTRAL, or PROMOTER (weights −5, +1, +5), and the book embedding is added to the user vector with the corresponding scale, then renormalized. Cold-start is handled by collecting genre preferences at registration, publishing a `create_user_preference` event, and seeding the profile vector before the first recommendation query.

v4 focuses on production-grade distributed-systems concerns: idempotent consumers, transactional outbox, Flyway migrations, correlation ID propagation, and Testcontainers-based integration tests for full distributed flows.

**Demonstrates**
- Event-Carried State Transfer over Kafka — five services, each owning its read models
- Deliberate ownership boundaries: catalog-service as canonical writer of book-progress; engagement-service replicates history via events, never overrides operational state
- JVM-native semantic retrieval — LangChain4j all-MiniLM-L6-v2, 384-dim L2-normalized vectors, HNSW indexing
- Incremental user profile learning from rating signals, with cold-start fallback to popularity ranking
- Kafka retry topics and Dead Letter Topics — 3 attempts, fixed 3s backoff, DLT as operational signal
- Reactive API Gateway with Spring WebFlux, JWT validation, and Redis-backed per-route rate limiting

`Java 21 · Spring Boot · Spring WebFlux · Kafka · PostgreSQL · pgvector · Redis · LangChain4j · Docker`

---

### [Kairos](https://github.com/Luca5Eckert/Kairos) · operational v1

JVM-native graph-augmented retrieval engine that turns documents into a semantic memory graph. The idea: *Obsidian where the graph builds itself* — the user feeds the system; Kairos extracts concepts, relations, and semantic structure automatically.

The architecture is a dual store. PostgreSQL/pgvector holds chunk embeddings and concept embeddings for dense retrieval. Neo4j holds the knowledge graph: PhraseNodes, PassageNodes, TRIPLE edges (subject–predicate–object), SYNONYMY edges between semantically equivalent phrases, and CONTEXT edges linking passages to the concepts they contain. At ingestion, each chunk is embedded locally via ONNX Runtime (all-MiniLM-L6-v2, 384 dimensions, no Python sidecar), Gemini Flash extracts factual triples through an OpenIE port, and SYNONYMY edges are created by comparing new phrase embeddings against existing ones — anything above 0.8 cosine similarity gets linked, connecting variants like "backprop" and "backpropagation" automatically.

At query time, pgvector retrieves semantic anchors in both phrase and passage space, those anchors seed a Neo4j GDS Personalized PageRank run that expands through related concepts and passages, dense retrieval runs in parallel, and results are fused by RRF. Node specificity — modeled as `1 / log(1 + document_frequency)` — prevents generic concepts from dominating propagation.

Current v1 work closes the gap to HippoRAG 2.0: passage-aware weighted PPR, triple recall with recognition memory filtering, per-user graph isolation via OAuth2, and retrieval trace persistence as the foundation for future learning-to-rank.

**Demonstrates**
- Backend-first retrieval infrastructure — not notebook-based ML experimentation
- JVM-native embedding pipeline with ONNX Runtime — no Python sidecar
- Dual-store architecture: pgvector for dense retrieval, Neo4j for graph traversal and PPR
- HippoRAG 2.0-style retrieval: semantic anchors → Personalized PageRank → dense fallback → RRF fusion
- SYNONYMY edges computed from embedding similarity — lexical variation handled structurally
- LLM (Gemini Flash) isolated to triple extraction behind a swappable domain port
- Hexagonal architecture: domain has no framework dependencies; infrastructure implements domain-defined ports

`Java 21 · Spring Boot · Spring AI · ONNX Runtime · PostgreSQL · pgvector · Neo4j · Neo4j GDS · Gemini · Docker`

---

### [OpenIT](https://github.com/Luca5Eckert/OpenIt) · delivered

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

Graph-based social network backend built around Neo4j relationships and modular backend architecture. Models people, connection requests, accepted bidirectional relationships, posts, and network visualization endpoints.

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
