# Lucas Eckert

Backend developer focused on Java, Spring Boot, event-driven systems, and observability.

I work on backend systems where data ownership, state transitions, integration contracts, and failure visibility are explicit.

[Portfolio](https://lucas-eckert.vercel.app) · [LinkedIn](https://linkedin.com/in/lucas-ismael-eckert) · [Email](mailto:lucasismaeleckert@gmail.com)

## Evidence

- **Portal Conecta:** backend technical reference for the central Hub Core; one team release was validated by **682 Maven tests with 0 failures and 0 errors**.
- **VellumHub:** **478 Maven tests passing**; local recommendation benchmark moved from approximately **300-500 ms to 80-120 ms** after replacing a Python sidecar with in-process JVM embeddings and pgvector.
- **Kairos:** latest local run executed **244 tests with 0 failures and 0 errors**; JaCoCo reports **86.77% line coverage and 74.54% branch coverage**.

The Portal Conecta test total is a team-system result. VellumHub latency is a local project benchmark, not a production SLA. Kairos coverage measures implementation quality, not retrieval relevance.

## Current work

I am completing the WEG/CentroWEG-SENAI Systems Development Apprenticeship Program, combining technical coursework with applied team delivery.

My strongest work is concentrated in:

- backend APIs and domain rules;
- authentication and contextual authorization;
- service and data ownership boundaries;
- Kafka and RabbitMQ messaging;
- API Gateway, structured logging, traces, metrics, and dashboards;
- PostgreSQL/pgvector and Neo4j-backed retrieval.

## Selected projects

### [Portal Conecta](https://github.com/Portal-Conecta)

A modular academic platform whose central backend owns shared identity, academic structure, permissions, service contracts, and operational concerns.

**My scope:** Hub Core boundaries, selected domain flows, API Gateway behavior, reusable request logging, RabbitMQ integration, OpenAPI contracts, and Grafana/Loki/Prometheus/Tempo/Alloy observability.

**Concrete delivery:** administrative user and class imports in CSV/XLSX with dry-run and `REJECT`/`SKIP` policies, reusing existing use cases to preserve authorization, validation, and domain events.

[Read the case study](case-studies/portal-conecta.md).

### [VellumHub](https://github.com/Luca5Eckert/VellumHub)

An event-driven recommendation backend where serving reads from recommendation-owned state instead of synchronously calling catalog, user, and engagement services.

**Decision:** propagate upstream changes through Kafka and materialize local PostgreSQL/pgvector read models.

**Result:** zero synchronous upstream fan-out in the recommendation hot path, 478 passing Maven tests, and a local benchmark improvement from roughly 300-500 ms to 80-120 ms after removing a Python sidecar.

`Java 21 · Spring Boot · Kafka · PostgreSQL · pgvector · Redis · OpenTelemetry · Prometheus · Grafana · Loki · Tempo`

### [Kairos](https://github.com/Luca5Eckert/Kairos)

A JVM-native graph-augmented retrieval backend combining dense passage recall, triple recall, constrained Recognition Memory, and user-scoped Personalized PageRank.

**Decision:** replace isolated concept candidates with triple-based recognition seeds while keeping graph expansion stable.

**Result:** retrieval returns ranked chunks plus activated triples as evidence. Latest local verification: 244 tests, 86.77% line coverage, and 74.54% branch coverage.

`Java 21 · Spring Boot · ONNX Runtime · PostgreSQL · pgvector · Neo4j GDS · Spring AI · Gemini`

### [OpenIt](https://github.com/Luca5Eckert/OpenIt)

An IoT payment and access-control flow integrating ESP32, MQTT, Node-RED, Spring WebFlux, MySQL, Mercado Pago, and SSE.

**Core rule:** the gate opens only after payment confirmation has been persisted and validated by the backend.

## Technical focus

**Backend:** Java 17/21, Spring Boot, Spring MVC, Spring WebFlux, Spring Security, REST, OpenAPI  
**Data:** PostgreSQL, pgvector, MySQL, Neo4j GDS, Redis  
**Messaging:** Kafka, RabbitMQ, MQTT  
**Quality:** JUnit 5, Mockito, Testcontainers, JaCoCo, Maven, Flyway  
**Operations:** Docker, GitHub Actions, OpenTelemetry, Prometheus, Grafana, Loki, Tempo, Alloy  
**Retrieval:** ONNX Runtime, Spring AI, Gemini, vector search, graph-augmented retrieval

## What I am looking for

Junior backend or software engineering roles where Java, system boundaries, messaging, data modeling, testing, and operational visibility matter.
