# Lucas Eckert

Backend developer focused on Java/Spring systems with explicit state ownership, event-driven integration, observability, and failure-safe flows.

[Portfolio](https://lucas-eckert.vercel.app) · [LinkedIn](https://www.linkedin.com/in/lucas-ismael-eckert) · [Email](mailto:lucasismaeleckert@gmail.com)

## Current work

I am part of the WEG/CentroWEG-SENAI Systems Development Apprenticeship Program, combining technical coursework with applied team-based software delivery.

My main backend scope is **Portal Conecta**, a modular academic platform. I work across Hub Core boundaries, API contracts, authorization, administrative imports, API Gateway behavior, reusable logging, RabbitMQ integration, and observability.

## Proof points

- **Portal Conecta:** authored merged CSV/XLSX import flows for users and classes with dry-run validation and explicit `REJECT`/`SKIP` conflict policies. A Hub Core release was validated by **682 Maven tests with no failures or errors**; this is a team-system result.
- **VellumHub:** moved recommendation serving to Kafka-fed local read models and replaced a Python sidecar with in-process JVM embeddings and pgvector/HNSW search, reducing a local benchmark from approximately **300–500 ms to 80–120 ms**. Latest consolidated validation: **478 Maven tests passing**.
- **Kairos:** reworked graph seed selection from isolated concept candidates to passage recall, triple recall, constrained Recognition Memory, and user-scoped Personalized PageRank. Latest local verification: **244 tests executed**, **86.77% line coverage**, and **74.54% branch coverage**.

## Selected systems

### [Portal Conecta](case-studies/portal-conecta.md)

A team-built modular academic platform where a central Hub Core owns shared identity, academic structure, permissions, and integration contracts.

My individually attributable work includes:

- [user import through CSV/XLSX](https://github.com/Portal-Conecta/core-backend/pull/293), including dry-run, conflict policies, permission preservation, and post-commit activation behavior;
- [class import through CSV/XLSX](https://github.com/Portal-Conecta/core-backend/pull/296), reusing the existing creation use case to preserve validation and events;
- contributions across gateway, request correlation, trace propagation, reusable access logging, and the Grafana/Loki/Prometheus/Tempo/Alloy observability stack.

`Java 21 · Spring Boot · Spring Security · PostgreSQL · RabbitMQ · Spring Cloud Gateway · OpenAPI · OpenTelemetry`

### [VellumHub](https://github.com/Luca5Eckert/VellumHub)

An event-driven recommendation backend that serves from recommendation-owned PostgreSQL/pgvector state instead of calling catalog, user, and engagement services during the request path.

Key decisions:

- service-owned databases;
- Event-Carried State Transfer through Kafka;
- local recommendation read models;
- retry topics and Dead Letter Topics;
- gateway plus downstream JWT validation;
- optional local metrics, logs, and traces stack.

`Java 21 · Spring Boot · Kafka · PostgreSQL · pgvector · Redis · OpenTelemetry · Grafana`

### [Kairos](https://github.com/Luca5Eckert/Kairos)

A JVM-native graph-augmented retrieval backend that combines local ONNX embeddings, passage and triple retrieval in pgvector, constrained Gemini recognition, and Neo4j GDS graph propagation.

Key decisions:

- PostgreSQL as durable text and semantic source of truth;
- Neo4j as a user-scoped graph projection;
- LLM usage isolated behind ports for extraction and finite candidate selection;
- ranked chunks returned with activated triples as evidence;
- no claims of retrieval-quality improvement without a labeled benchmark.

`Java 21 · Spring Boot · ONNX Runtime · PostgreSQL · pgvector · Neo4j GDS · Spring AI`

### [OpenIt](https://github.com/Luca5Eckert/OpenIt)

An IoT access-control and payment flow where the backend persists Mercado Pago confirmation before sending a gate command through Node-RED, MQTT, and ESP32. SSE updates the terminal without making frontend state the authority for physical access.

`Java 21 · Spring WebFlux · MySQL · MQTT · Node-RED · Mercado Pago · React · TypeScript`

## Engineering focus

- API and domain boundaries
- event-driven systems and local read models
- PostgreSQL, pgvector, and Neo4j
- authorization and source-of-truth modeling
- automated testing and migration safety
- structured logging, metrics, traces, and runbooks
- retrieval and recommendation infrastructure

## Core stack

| Area | Technologies |
|---|---|
| Backend | Java 17/21, Spring Boot, Spring MVC, Spring WebFlux, Spring Security, REST, JWT, OpenAPI |
| Data | PostgreSQL, pgvector/HNSW, MySQL, Redis, Neo4j, Neo4j GDS |
| Messaging | Kafka, RabbitMQ, MQTT |
| Quality | JUnit 5, Mockito, Testcontainers, JaCoCo, Maven, Flyway, GitHub Actions |
| Observability | OpenTelemetry, Micrometer, Prometheus, Grafana, Loki, Tempo, Alloy |
| Retrieval | ONNX Runtime, Spring AI, Gemini, dense retrieval, triple recall, Personalized PageRank |
| Infrastructure | Docker, Docker Compose, Linux, AWS |

## Current direction

- hardening VellumHub around event contracts, idempotency, outbox publication, migrations, tracing, and distributed-flow tests;
- expanding Kairos with failed-chunk recovery, persisted retrieval traces, dense fallback behavior, and a labeled evaluation set;
- documenting engineering decisions as ADRs, PR narratives, and reproducible evidence instead of unsupported scale claims.

## Certifications

Confluent Data Streaming Engineer - Foundations · Neo4j Graph Data Science · Neo4j & Generative AI · AWS Academy Cloud Foundations · AWS Academy Generative AI Foundations
