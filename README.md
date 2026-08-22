# Lucas Eckert

**Backend Developer | Java/Spring | Distributed and data-intensive systems**

I build backend systems where state remains correct under partial failure, asynchronous processing, and eventually consistent infrastructure.

My work focuses on explicit data ownership, durable write paths, derived read models, observable services, and APIs with clear operational boundaries.

[Portfolio](https://lucas-eckert.vercel.app) · [LinkedIn](https://linkedin.com/in/lucas-ismael-eckert) · [Email](mailto:lucasismaeleckert@gmail.com)  
Jaraguá do Sul, Brazil · BRT / UTC-03 · English B2

---

## Current role

I work at **WEG** as a **Software Developer** in **Industrial Software Engineering / Integrated Manufacturing Systems**, building and integrating software that supports manufacturing processes.

My work currently spans backend development, system integration, data flows, frontend integration, code review, testing, and application delivery to corporate Kubernetes environments.

Recent work includes:

- **Designed and developed a Java/Spring Boot geolocation service from the ground up**, separating location responsibilities between manufacturing systems. The service exposes REST APIs for position history and last-known-location queries and supports authenticated WebSocket ingestion for tracker telemetry, backed by PostgreSQL, Flyway, JUnit, and Testcontainers.
- **Optimized large checklist workflows containing around 300 questions**, restructuring item-level state updates and rendering behavior to reduce interaction time from approximately **1.5 s to 45 ms**.
- Delivered cross-service features across an internal checklist platform built with **React/TypeScript, NestJS/PostgreSQL, and FastAPI/Python**, keeping contracts, database migrations, historical data, and Excel import/export behavior compatible across services.
- Implemented a **location answer type** supporting GPS capture, interactive map selection, manual coordinates, and local offline persistence, later integrating internal manufacturing locations with an OpenStreetMap fallback.
- Extended the checklist platform with additional domain-specific question types and reusable entity/user selection flows while preserving behavior across the editor, responder, stored answers, and Excel workflows.
- Perform code review and application delivery through **CI/CD and Kubernetes**, including deploying the Excel service to production and Checklist features to QAS.

The work sits inside an industrial software engineering team that creates software around manufacturing operations and integrates applications with data originating from manufacturing systems and MES-related flows.

Previously, during the **CentroWEG/SENAI Industrial Apprenticeship Program**, I served as backend technical lead for Portal Conecta, a multi-service platform developed by more than 20 contributors.

---

## Selected evidence

- **WEG — Industrial Software Engineering:** designed a Java/Spring Boot geolocation service with REST and authenticated WebSocket ingestion; delivered cross-service functionality across React, NestJS, PostgreSQL, and FastAPI; optimized ~300-question checklist interactions from approximately **1.5 s to 45 ms**; and delivered applications through CI/CD to Kubernetes-based QAS and production environments.
- **Portal Conecta:** backend technical leadership across a platform with more than 20 contributors, eight repositories, and five services; the Hub Core recorded **779 passing tests**.
- **VellumHub:** moved recommendation serving from a Python sidecar to JVM-native embeddings and pgvector, reducing local benchmark latency from approximately **300–500 ms to 80–120 ms**, with **478 Maven tests**; infrastructure includes Kubernetes, Kustomize, and Argo CD GitOps definitions.
- **Kairos:** built a graph-augmented retrieval backend validated by **262 tests**, with **87.15% line coverage** and **73.00% branch coverage**, plus Terraform-modeled AWS infrastructure.

---

## Selected work

### [VellumHub](https://github.com/Luca5Eckert/VellumHub) — Event-Driven Recommendation Platform

A distributed recommendation backend that serves personalized results entirely from recommendation-owned state instead of querying catalog, user, and engagement services during each request.

- **Architecture:** designed service-owned databases and Kafka-fed read models using Event-Carried State Transfer. Catalog, user, rating, progress, and reaction events are materialized into local recommendation projections.
- **Serving path:** recommendations use locally stored book embeddings, user-profile vectors, interaction history, and pre-joined metadata, avoiding synchronous fan-out in the request path.
- **Reliability:** implemented transactional outbox flows, idempotent consumers, retry and dead-letter handling, Flyway migrations, correlation propagation, distributed tracing, and Testcontainers-based validation.
- **Delivery:** modeled Kubernetes desired state with Kustomize overlays for local and production environments and an Argo CD pull-based GitOps flow using immutable image references and explicit rollout/rollback behavior.
- **Evidence:** replaced an external Python embedding service with in-JVM embeddings and pgvector HNSW search, reducing local benchmark latency from approximately **300–500 ms to 80–120 ms**. Consolidated validation covers **478 Maven tests**.

`Java 21 · Spring Boot · Kafka · PostgreSQL · pgvector · Redis · Flyway · OpenTelemetry · Testcontainers · Docker · Kubernetes · Kustomize · Argo CD`

---

### [Kairos](https://github.com/Luca5Eckert/Kairos) — Graph-Augmented Retrieval Engine

A personal-knowledge backend that combines semantic retrieval with graph-based context expansion to retrieve evidence connected through passages, concepts, and extracted relationships.

- **Data ownership:** PostgreSQL and pgvector store durable sources, chunks, embeddings, triples, processing state, and retrieval history as the source of truth. Neo4j operates as a derived graph projection.
- **Retrieval:** combines dense passage recall, triple recall, graph-seed selection, weighted Personalized PageRank, and ranking fusion to support multi-hop context discovery.
- **AI pipeline:** runs `all-MiniLM-L6-v2` embeddings locally on the JVM through ONNX Runtime and DJL. Gemini is integrated through Spring AI for structured triple extraction and constrained graph-seed selection.
- **Reliability:** persists ingestion state before asynchronous enrichment, tracks explicit per-chunk progress, and retries failed work idempotently without discarding completed processing.
- **Infrastructure:** modeled an AWS development foundation with Terraform, including VPC, EC2 managed through SSM without SSH, encrypted EBS, ECR, IAM boundaries, and remote S3 state.
- **Evidence:** validated by **262 tests**, Testcontainers, **87.15% line coverage**, **73.00% branch coverage**, container smoke testing, CodeQL, Trivy, and SBOM generation.

`Java 21 · Spring Boot · Spring AI · ONNX Runtime · PostgreSQL · pgvector · Neo4j GDS · Gemini · Testcontainers · Terraform · AWS`

---

### [Portal Conecta](https://github.com/Portal-Conecta) — Multi-Service Academic Platform

A team platform in which a central backend owns identity, academic structure, permissions, integration contracts, and shared operational infrastructure.

I served as backend technical lead during the CentroWEG/SENAI final project, developed by more than 20 contributors across eight repositories and five services.

- **Service boundaries:** defined the Hub Core as the source of truth for authentication, users, courses, classes, academic memberships, rooms, notifications, and contextual authorization.
- **Core capabilities:** implemented administrative CSV/XLSX imports for users and classes, including `dryRun`, `REJECT/SKIP` policies, duplicate handling, permission preservation, and reuse of existing domain use cases.
- **Integration:** established explicit OpenAPI contracts and RabbitMQ event flows between the Hub Core and feature services such as Checklist, Seat Map, and Announcements.
- **Platform foundation:** owned the WebFlux API Gateway and shared operational infrastructure, including JWT validation, Redis-backed rate limiting, correlation IDs, W3C trace propagation, reusable MVC/WebFlux logging, and observability with Prometheus, Grafana, Loki, Tempo, and Alloy.
- **Evidence:** the Hub Core recorded **779 passing tests** in a verified Maven execution.

`Java 21 · Spring Boot · Spring Security · Spring Cloud Gateway · PostgreSQL · Redis · RabbitMQ · OpenAPI · OpenTelemetry · Grafana · Loki · Tempo`

---

## Engineering focus

**Backend and APIs**  
Java 21 · Spring Boot · Spring MVC · Spring WebFlux · Spring Security · NestJS · FastAPI · REST · JWT · OpenAPI · Maven

**Data and messaging**  
PostgreSQL · pgvector · Neo4j GDS · Redis · MySQL · Kafka · RabbitMQ · Flyway

**Distributed systems**  
Explicit data ownership · Event-Carried State Transfer · derived read models · transactional outbox · idempotent consumers · eventual consistency · retry and dead-letter handling · partial-failure recovery

**Quality and delivery**  
JUnit 5 · Mockito · Testcontainers · JaCoCo · GitHub Actions · CI/CD · Docker · CodeQL · Trivy · CycloneDX/SBOM

**Observability**  
OpenTelemetry · Micrometer · Prometheus · Grafana · Loki · Tempo · Alloy · structured logging · distributed tracing

**AI and retrieval**  
ONNX Runtime · Spring AI · LangChain4j · Gemini · embeddings · vector search · graph-augmented retrieval · Personalized PageRank

**Cloud and infrastructure**  
Kubernetes · Kustomize · Argo CD · AWS · Terraform · EC2 · EBS · ECR · VPC · IAM · S3 · SSM

---

## Certifications

- Confluent Data Streaming Engineer — Foundations
- Apache Kafka Fundamentals Accreditation
- Neo4j Graph Data Science
- Neo4j and Generative AI
- Neo4j Fundamentals
- AWS Academy Cloud Foundations
- AWS Academy Generative AI Foundations

---

## Professional focus

I am focused on backend and data-intensive systems where correctness, explicit ownership, asynchronous integration, recoverability, and operational visibility matter.

My main areas of interest are distributed platforms, event-driven architectures, recommendation systems, retrieval infrastructure, data pipelines, system integration, and applied AI backends.
