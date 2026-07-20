# Lucas Eckert

I build backend systems where state stays correct even when infrastructure is slow, unavailable, or eventually consistent.

My work is centered on explicit ownership of data, durable write paths, derived read models, observable services, and APIs with clear operational boundaries.

[Portfolio](https://lucas-eckert.vercel.app) - [LinkedIn](https://linkedin.com/in/lucas-ismael-eckert) - [Email](mailto:lucasismaeleckert@gmail.com)  
Brazil - BRT / UTC-03

---

## Proof points

- **Kairos:** latest recorded local run: 251 tests; 86.77% line coverage and 74.54% branch coverage.
- **VellumHub:** recommendation serving moved from a Python sidecar to in-JVM pgvector, from ~300-500 ms to ~80-120 ms in local benchmarks.
- **Portal Conecta backend core:** release validation recorded 682 tests, 0 failures, 0 errors; the central backend work also includes API Gateway routing/security, reusable logging, and a Grafana/Loki/Prometheus/Tempo/Alloy observability stack.

---

## Currently

**At WEG** - CentroWEG / SENAI Industrial Apprenticeship Program, a Brazilian industry-linked technical apprenticeship program connected to WEG and SENAI training.  
Acting as backend technical lead on **Portal Conecta**, focused on the central backend: Hub Core, API Gateway, shared logging, observability, service contracts, authentication/authorization, RabbitMQ messaging, and synchronous/asynchronous integration boundaries.

**Personal**  
Hardening **VellumHub v4** around Kafka contracts, idempotent consumers, transactional outbox, Flyway migrations, tracing, and distributed-flow tests. Maintaining **Kairos** as a graph-augmented retrieval backend with local JVM embeddings, pgvector, Neo4j GDS, triple recall, and user-scoped graph propagation.

---

## Projects

### [VellumHub](https://github.com/Luca5Eckert/VellumHub) - event-driven book recommendation

A book recommendation backend that serves personalized results from local, event-fed state instead of calling every source service during the request.

**Problem:** recommendation systems that query catalog, user, and engagement services at serving time create synchronous coupling. One slow source service can degrade the whole recommendation path.

**Decision:** `recommendation-service` does not call upstream services during the hot path. Catalog, user, and engagement changes propagate through Kafka and materialize into recommendation-owned tables: book embeddings, user profile vectors, interacted books, and pre-joined metadata.

**Notable decisions:**
- Event-Carried State Transfer for local read models.
- PostgreSQL + pgvector with 384-dimensional embeddings and HNSW cosine search.
- Incremental user-profile updates from rating events classified as `DETRACTOR`, `NEUTRAL`, or `PROMOTER`.
- Cold-start profile seeding from onboarding genre preferences.
- Retry topics and Dead Letter Topics for inspectable async failures.
- Gateway-enforced JWT validation, Redis-backed rate limits, and downstream JWT validation.
- Local observability with Micrometer, Prometheus, Grafana, Loki, Tempo, Alloy, OpenTelemetry, dashboards, alerts, and runbooks.

**Result:** recommendation requests are served from the recommendation database alone, with catalog/user/engagement changes already folded into local projections. The pgvector path measures ~80-120 ms in-JVM versus ~300-500 ms with the previous Python sidecar.

`Java 21 - Spring Boot - Spring WebFlux - Spring Cloud Gateway - Kafka - PostgreSQL - pgvector - Redis - LangChain4j - Micrometer - Prometheus - Grafana - Loki - Tempo - OpenTelemetry - Docker`

---

### [Kairos](https://github.com/Luca5Eckert/Kairos) - graph-augmented retrieval engine

A personal knowledge backend that retrieves connected ideas, not just text chunks that look similar in embedding space.

**Problem:** standard vector RAG is good at semantic similarity, but weak when the useful context depends on relationships between passages, concepts, and extracted facts.

**Decision:** split retrieval across the stores that match the job. PostgreSQL + pgvector answers "what is semantically close to this query?" over durable text, passage embeddings, triple embeddings, and dense recall. Neo4j + Graph Data Science answers "what else does the graph connect to these anchors?" through `Passage` nodes, `PhraseNode` concepts, `CONTAINS` links, and `TRIPLE` relationships. Gemini is isolated behind Spring AI ports for triple extraction and recognition-memory seed selection; embeddings run locally through ONNX Runtime with `all-MiniLM-L6-v2`.

**Notable decisions:**
- Passage recall, triple recall, recognition-memory filtering, and Personalized PageRank.
- Reciprocal Rank Fusion over semantic and graph signals.
- User-scoped graph modeling as a first-class constraint, not a late `WHERE` clause.
- Authenticated source ingestion resolves ownership from request context, not client-submitted IDs.
- Graph retrieval returns activated triples as evidence beside ranked chunks.

**Result:** a user can ingest a source, let the system extract triples and build graph structure asynchronously, then query across semantic candidates and graph-expanded context. The backend has 251 tests; JaCoCo reports 86.77% line coverage and 74.54% branch coverage.

`Java 21 - Spring Boot - Spring AI - ONNX Runtime - PostgreSQL - pgvector - Neo4j - Neo4j GDS - Gemini - Flyway - Docker`

---

### [Portal Conecta](https://github.com/Portal-Conecta) - CentroWEG final project (team project)

A modular academic platform where the central backend owns identity, academic structure, permissions, integration contracts, and observability.

**Problem:** if every module keeps its own version of users, courses, classes, rooms, and permissions, the platform drifts into duplicated rules and inconsistent authorization.

**Decision:** build a central **Hub Core** as the official source of truth for shared academic data and authorization rules. Feature services such as Checklist, Seat Map, and Announcements stay outside that core boundary and integrate through explicit HTTP contracts, RabbitMQ events, and the API Gateway.

**Notable decisions:**
- Backend team scope centered on Hub Core, API Gateway, `portal-logging`, and observability rather than feature modules owned by other teams.
- Hub Core is the source of truth for authentication, users, profiles, courses, classes, memberships, rooms, notifications, and contextual authorization.
- OpenAPI contracts and RabbitMQ event flows make integrations explicit instead of coupling services through shared assumptions.
- API Gateway centralizes external routing, rate-limit policy, security, error shaping, correlation ID handling, and W3C trace propagation.
- `portal-logging` extracts servlet/reactive access logging, correlation IDs, user ID resolution, and health/metrics log suppression into a reusable package for services.
- Observability stack provisions Grafana, Loki, Prometheus, Tempo, and Alloy, with dashboards for Hub Core and JVM/Prometheus runtime metrics.
- Frontend work was secondary but real: contributed to integration points in the Next.js frontend when backend contracts needed to be reflected in the UI.

**Result:** feature teams could integrate through one central identity/academic-data backend, one gateway boundary, one shared logging package, and one observability stack instead of rebuilding those concerns per module. Hub Core release validation covered 682 tests, 0 failures, 0 errors, and 20 Docker/Testcontainers-dependent tests skipped; API Gateway has 21 source-level test scenarios across routing, security, rate limiting, and trace propagation; `portal-logging` has 50 source-level test scenarios across servlet/reactive access logs, correlation IDs, auto-configuration, and user ID resolution; observability includes 5 telemetry components and 2 provisioned Grafana dashboards.

`Java 21 - Spring Boot - Spring Security - Spring Cloud Gateway - PostgreSQL - RabbitMQ - OpenAPI - Docker - Grafana - Prometheus - Loki - Tempo - Alloy - OpenTelemetry`

---

### [OpenIT](https://github.com/Luca5Eckert/OpenIt) - IoT access control

An IoT parking flow where a physical gate opens only after the backend has confirmed and persisted payment state.

**Problem:** IoT payment flows that release a gate based on optimistic UI state create a state gap between what the user sees and what the backend has durably recorded.

**Decision:** access release is gated on persisted backend payment confirmation. The flow connects ESP32 sensors, MQTT, Node-RED, Spring WebFlux, Mercado Pago, MySQL, and a React/TypeScript terminal. Server-Sent Events push payment status to the frontend without client polling.

**Notable decisions:**
- MQTT events from ESP32 devices for vehicle detection.
- Node-RED as the IoT orchestration bridge.
- Spring backend as the authority for payment and access state.
- Mercado Pago integration behind a payment provider port.
- SSE for unidirectional real-time payment updates.
- Clean Architecture and bounded backend modules for access and payment.

**Result:** entry is recorded, payment is created, Mercado Pago confirmation updates backend state, and the exit command is sent to Node-RED/MQTT only after confirmed payment.

`Java 21 - Spring Boot - Spring WebFlux - MySQL - MQTT - ESP32 - Node-RED - Mercado Pago - React - TypeScript - Docker`

---

## Stack

**Languages**  
Java - SQL - TypeScript - JavaScript - Python

**Backend & APIs**  
Spring Boot - Spring MVC - Spring WebFlux - Spring Security - Spring Cloud Gateway - JPA/Hibernate - OpenAPI

**Frontend**  
React - Next.js - TypeScript

**Data & storage**  
PostgreSQL - pgvector - Neo4j - Neo4j GDS - Redis - MySQL

**Messaging & integration**  
Kafka - RabbitMQ - MQTT

**Observability**  
Micrometer - Prometheus - Grafana - Loki - Tempo - Alloy - OpenTelemetry

**AI & retrieval**  
Spring AI - LangChain4j - ONNX Runtime - Gemini

**Quality, delivery & runtime**  
JUnit 5 - Mockito - Testcontainers - JaCoCo - Maven - Flyway - Docker/Compose - GitHub Actions - Linux

**Cloud**  
AWS

---

## Engineering concepts

**Event-driven systems**  
Event-Carried State Transfer - transactional outbox - idempotent consumers - retry topics - dead letter topics - correlation ID propagation - eventual consistency - partial failure handling

**Data modeling & ownership**  
Service-owned persistence - write/read model separation - derived data - local read models - schema evolution - source-of-truth boundaries

**Architecture**  
Hexagonal Architecture - Clean Architecture - Domain-Driven Design - bounded contexts - CQRS - ports and adapters

**Retrieval & recommendation**  
RAG - graph-augmented retrieval - dense passage recall - triple recall - recognition memory - Personalized PageRank - Reciprocal Rank Fusion

**Backend quality**  
Integration testing - migration safety - observability - distributed tracing - structured logging - failure-safe flows

---

## Certifications

- Confluent Certified Data Streaming Engineer - Foundations
- Confluent Apache Kafka Fundamentals Accreditation
- Neo4j Graph Data Science Certification
- Neo4j & Generative AI Certification
- Neo4j Fundamentals
- AWS Academy - Cloud Foundations
- AWS Academy - Generative AI Foundations

Coursework through CentroWEG / SENAI: API Programming, Database Implementation, System Architecture, Cloud Computing, and Information Security.

---

## What I'm looking for

Backend and data-intensive systems roles where ownership and operational visibility matter: distributed systems, event-driven platforms, retrieval infrastructure, recommendation systems, data pipelines, and applied AI backends.

I am early-career by title, but I am looking for junior roles or internships where I can keep owning backend boundaries, making tradeoffs explicit, and turning complex domain rules into maintainable services.
