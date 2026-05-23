# Lucas Eckert

Backend developer focused on data-intensive backend systems: graph-augmented retrieval engines, event-driven recommendation pipelines, and distributed infrastructure designed around explicit state, derived data, and safe failure handling.

My work sits at the intersection of **backend engineering**, **data modeling**, and **applied ML/AI**. I am interested in how retrieval, embeddings, and knowledge graphs become production backend infrastructure — systems with explicit write models, domain events, local read models, storage boundaries, and observable behavior.

[Portfolio](https://lucas-eckert.vercel.app) · [LinkedIn](https://linkedin.com/in/lucas-ismael-eckert) · [GitHub](https://github.com/Luca5Eckert) · [Email](mailto:lucasismaeleckert@gmail.com)

---

## Currently

Completing WEG's **CentroWEG / SENAI Industrial Apprenticeship Program** in Systems Development, with current backend work centered on service-oriented architecture, distributed-system reliability, and graph-augmented retrieval.

* Leading backend architecture for **Portal Conecta**, focused on service boundaries, OpenAPI contracts, RabbitMQ messaging, and explicit synchronous/asynchronous integration.
* Evolving **VellumHub v4** with idempotent consumers, transactional outbox, Flyway migrations, correlation ID propagation, observability, and Testcontainers-based distributed-flow tests.
* Refining **Kairos v1** toward HippoRAG 2.0-style retrieval: passage-aware weighted PageRank, recognition memory filtering, triple recall, per-user graph isolation, and retrieval trace persistence.
* Studying distributed systems and derived data through *Designing Data-Intensive Applications* and applied Java/Spring work.

---

## Selected Systems

### [VellumHub](https://github.com/Luca5Eckert/VellumHub) · mature v3 · v4 in progress

Event-driven recommendation platform designed to serve personalized recommendations without query-time coupling to source-of-truth services.

Five microservices — gateway, user, catalog, engagement, and recommendation — each own their domain and database. The central architectural decision is that recommendation-service never calls catalog-service at query time. Instead, it maintains local read models fed by Kafka events: book embeddings, user profile vectors, and pre-joined metadata. Every recommendation response is served from local state, removing synchronous cross-service coupling from the hot path.

Recommendations are served through a CTE query over pgvector. ANN search via HNSW over 384-dimensional L2-normalized embeddings generates candidate books, then results are reranked with a weighted blend of vector similarity and popularity score. User profiles are updated incrementally from rating events: each rating is classified as `DETRACTOR`, `NEUTRAL`, or `PROMOTER`, the book embedding is scaled accordingly, added to the user vector, and renormalized.

Cold-start is handled at registration. Genre preferences are collected, a `create_user_preference` event is published, and the profile vector is seeded before the first recommendation query.

v4 focuses on production-grade distributed-systems concerns: transactional outbox to prevent database/Kafka dual-write failure, idempotent consumers to make retries and reprocessing safe, Flyway migrations for schema evolution, correlation ID propagation across services, observability, and Testcontainers-based integration tests for full distributed flows, including failure and retry paths.

**Key decisions**

* Read model isolation via Event-Carried State Transfer: recommendation-service owns derived copies of the data it needs to serve recommendations locally.
* Transactional outbox prevents phantom events and dual-write inconsistencies between the database and Kafka.
* Idempotent consumers with deduplication keys make Kafka retries, broker restarts, and consumer restarts safe at the application boundary.
* Incremental user profile learning updates recommendation state from rating signals without relying on batch recomputation.
* Cold-start is handled at write time through preference seeding, reducing the need for degraded query-time fallback behavior.
* Service ownership boundaries are explicit: source-of-truth services own writes; downstream services consume events to build derived read models.

`Java 21 · Spring Boot · Spring WebFlux · Kafka · PostgreSQL · pgvector · Redis · LangChain4j · Flyway · Docker · Testcontainers`

---

### [Kairos](https://github.com/Luca5Eckert/Kairos) · operational v1

JVM-native graph-augmented retrieval engine that turns documents into a semantic memory graph. The idea: *Obsidian where the graph builds itself* — the user feeds the system; Kairos extracts concepts, relations, and semantic structure automatically.

The architecture is a dual store. PostgreSQL/pgvector holds chunk and concept embeddings for dense retrieval. Neo4j holds the knowledge graph: `PhraseNode`s, `PassageNode`s, `TRIPLE` edges (subject–predicate–object), `SYNONYMY` edges between semantically equivalent phrases, and `CONTEXT` edges linking passages to the concepts they contain.

At ingestion, each chunk is embedded locally via ONNX Runtime using all-MiniLM-L6-v2 384-dimensional embeddings, with no Python sidecar. Gemini Flash extracts factual triples through an OpenIE-style domain port, and `SYNONYMY` edges are created by comparing new phrase embeddings against existing ones, linking lexical variants structurally instead of resolving them through query-time fuzzy matching.

At query time, pgvector retrieves semantic anchors in both phrase and passage space. Those anchors seed a Neo4j GDS Personalized PageRank run that expands through related concepts and passages; dense retrieval runs in parallel; results are fused with Reciprocal Rank Fusion. Node specificity, modeled as `1 / log(1 + document_frequency)`, prevents generic concepts from dominating propagation.

Current v1 work closes the gap to HippoRAG 2.0-style retrieval: passage-aware weighted PPR, triple recall with recognition memory filtering, per-user graph isolation via OAuth2, and retrieval trace persistence as the foundation for future learning-to-rank.

**Key decisions**

* Dual-store architecture separates retrieval concerns: pgvector handles dense vector search; Neo4j handles structural reasoning, concept propagation, and graph traversal.
* JVM-native embedding pipeline keeps retrieval infrastructure inside the backend runtime instead of depending on a Python sidecar.
* `SYNONYMY` edges are computed at ingestion time, so lexical variation is represented structurally in the graph.
* The LLM is isolated behind a swappable domain port for triple extraction, keeping provider-specific integration outside the domain model.
* Hexagonal architecture keeps the domain layer free of framework dependencies; infrastructure adapters implement domain-defined ports.
* Per-user graph isolation is treated as a first-class data modeling concern, not an authorization afterthought.

`Java 21 · Spring Boot · Spring AI · ONNX Runtime · PostgreSQL · pgvector · Neo4j · Neo4j GDS · Gemini · Docker`

---

### [OpenIT](https://github.com/Luca5Eckert/OpenIt) · delivered

Reactive IoT parking access-control system where backend-confirmed payment state controls physical access.

OpenIT coordinates ESP32 sensor events, MQTT communication, Node-RED orchestration, a Spring WebFlux backend, Mercado Pago Checkout Pro, MySQL persistence, and a React/TypeScript payment terminal. Delivered as a CentroWEG formative project, it covers full end-to-end backend ownership over hardware events, payment state, persistence, real-time updates, and access-control rules.

**Key decisions**

* Gate release is tied to persisted payment confirmation, not optimistic UI state, so physical access is driven by durable backend state.
* Server-Sent Events propagate payment status without frontend polling and without WebSocket overhead.
* Node-RED acts as an orchestration layer between IoT events and backend actions, keeping the Spring service free of hardware-specific flow logic.
* Access and payment concerns are separated through Clean Architecture / DDD-style boundaries.

`Java 21 · Spring Boot · Spring WebFlux · MySQL · MQTT · ESP32 · Node-RED · Mercado Pago · React · TypeScript · Docker`

---

### [Vinculo](https://github.com/Luca5Eckert/vinculo)

Graph-based social network backend built around Neo4j relationships and modular backend architecture. It models people, connection requests, accepted bidirectional relationships, posts, and network visualization endpoints.

**Key decisions**

* Neo4j is used deliberately for relationship-first social graph modeling instead of forcing traversal-heavy behavior through relational joins.
* Connection requests have an explicit lifecycle with accepted/rejected state transitions.
* Authentication and authorization are handled through JWT and role-based access control.
* Backend modules are separated across auth, person, connection, request, post, and graph concerns.

`Java 21 · Spring Boot · Neo4j · Spring Security · JWT · Docker · Testcontainers`

---

## Stack

**Languages** — Java (primary) · SQL · TypeScript · Python · JavaScript · C

**Backend** — Spring Boot · Spring WebFlux · Spring Security · Spring AI · REST APIs · JWT · SSE · JPA/Hibernate · JDBC · OpenAPI/Swagger

**Distributed Systems & Messaging** — Kafka · RabbitMQ · MQTT · Event-Carried State Transfer · Transactional Outbox Pattern · Idempotent Consumers · Retry Topics · Dead Letter Topics · Correlation ID Propagation

**Data & Storage** — PostgreSQL · pgvector · Neo4j · Neo4j GDS · Redis · MySQL · write/read model separation · derived data · schema evolution

**AI & Retrieval** — LangChain4j · ONNX Runtime · Gemini · RAG · Graph-Augmented Retrieval · Vector Search · Personalized PageRank · Reciprocal Rank Fusion · Embeddings

**Architecture** — Hexagonal Architecture · DDD · Bounded Contexts · Clean Architecture · Eventual Consistency · CQRS

**Infrastructure & Tooling** — Docker · Docker Compose · Flyway · GitHub Actions · Maven · Git · Linux · Testcontainers

**Testing** — JUnit 5 · Mockito · Testcontainers · JaCoCo

---

## Certifications & Coursework

* **Neo4j Graph Data Science Certification** — graph algorithms, graph projections, and graph-based data analysis.
* **Neo4j & Generative AI Certification** — knowledge graphs, retrieval workflows, and GenAI integration with graph data.
* **Neo4j Fundamentals** — graph data modeling, Cypher, and Neo4j core concepts.
* **AWS Academy Graduate — Generative AI Foundations** — foundational GenAI concepts and AWS-oriented AI workflows.
* **Relevant coursework at WEG CentroWEG / SENAI** — API Programming, Database Implementation, System Architecture, Cloud Computing, and Information Security.

---

## What I'm looking for

Backend or data-intensive systems engineering roles — ideally in teams working on distributed systems, retrieval infrastructure, data pipelines, or applied ML/AI backends.

I am interested in environments where correctness under partial failure is taken seriously, data modeling is a first-class concern, and backend systems are designed to evolve over time.

Open to junior positions and internships where I can contribute to production backend code from day one.

[Portfolio](https://lucas-eckert.vercel.app) · [LinkedIn](https://linkedin.com/in/lucas-ismael-eckert) · [GitHub](https://github.com/Luca5Eckert) · [Email](mailto:lucasismaeleckert@gmail.com)
