# Lucas Eckert

**Backend Developer | Java/Spring | Distributed and data-intensive systems**

I build backend systems around explicit boundaries, measurable performance, reliable integration, and recoverable state.

My professional work combines Java/Spring services, system integration, database performance, product discovery, testing, CI/CD, and application delivery in Kubernetes environments. In personal projects, I go deeper into event-driven reliability, recommendation infrastructure, and graph-augmented retrieval.

[Portfolio](https://lucas-eckert.vercel.app) · [LinkedIn](https://linkedin.com/in/lucas-ismael-eckert) · [Email](mailto:lucasismaeleckert@gmail.com)  
Jaraguá do Sul, Brazil · BRT / UTC-03 · English B2

---

## Current role

I work at **WEG** as a **Software Developer** in **Industrial Software Engineering / Integrated Manufacturing Systems**, developing and integrating internal software used in manufacturing workflows.

I participate in product discovery with analysts, then define and implement the technical solution across the services involved. Recent work includes:

- **Reduced an internal organizational lookup flow from 988 ms to 215 ms (-78%)** by removing sequential/N+1-style relationship loading, consolidating database access, and pushing filtering to the database over a directory with approximately **63,000 users, 6,000 sections, and 1,320 departments**. With a warm endpoint cache, recurring responses reach about **30 ms (-97% vs. baseline)**. The change was exercised locally and in Kubernetes-based QAS/production environments and validated against **281 automated tests**.
- **Designed and developed a Java/Spring Boot geolocation service from the ground up** for vehicle/driver tracking workflows. It exposes REST APIs for position history and last-known-location queries and authenticated WebSocket ingestion for tracker telemetry, backed by PostgreSQL, Flyway, JUnit, and Testcontainers.
- Delivered new checklist capabilities end to end across **React/TypeScript, NestJS/PostgreSQL, and FastAPI/Python**, including location and organizational-structure response types, persistence contracts, validation, PDF output, and Excel import/export compatibility. Real audit flows can contain around **300 questions**.
- Work through the application delivery cycle in **Kubernetes** and am currently building the Checklist automated testing / **CI/CD pipeline**; I have also deployed the Excel-processing service to production.

The geolocation service is the integration boundary I own. Mobile position publishing from Nexus is being implemented by another system/team, while the authenticated WebSocket path for JMAK-style tracker messages is implemented on the service side and awaits validation with the physical tracker.

Previously, during the **CentroWEG/SENAI Industrial Apprenticeship Program**, I served as backend technical lead for Portal Conecta, a multi-service platform developed by more than 20 contributors.

---

## Selected evidence

- **WEG — backend performance:** **988 ms → 215 ms (-78%)** after query/access-pattern changes; approximately **30 ms with warm cache** over organizational data containing ~63k users, 6k sections, and 1,320 departments.
- **WEG — service ownership:** designed a Java/Spring Boot geolocation service with REST position APIs, authenticated WebSocket telemetry ingestion, PostgreSQL/Flyway persistence, and Testcontainers integration coverage.
- **Portal Conecta:** backend technical leadership across more than 20 contributors, eight repositories, and five services, including the Hub Core, WebFlux API Gateway, contracts, security, and observability foundation.
- **VellumHub:** moved recommendation serving from an external Python embedding path to JVM-native embeddings and pgvector HNSW, reducing a local benchmark from approximately **300–500 ms to 80–120 ms**.
- **Kairos:** built a graph-augmented retrieval backend combining pgvector dense recall with Neo4j GDS Personalized PageRank, recoverable ingestion, JVM-local embeddings, and Terraform-modeled AWS infrastructure. A reproducible vector-vs-hybrid retrieval benchmark is now planned to measure Recall@K, MRR, NDCG, and latency.

---

## Selected work

### [VellumHub](https://github.com/Luca5Eckert/VellumHub) — Event-Driven Recommendation Platform

A distributed recommendation backend that serves personalized results from recommendation-owned state instead of synchronously querying catalog, user, and engagement services on every request.

- **Architecture:** service-owned databases and Kafka-fed read models using Event-Carried State Transfer.
- **Serving path:** locally materialized embeddings, user-profile vectors, interaction history, and pre-joined metadata avoid synchronous fan-out.
- **Reliability:** transactional outbox, idempotent consumers, retry/dead-letter handling, Flyway migrations, distributed tracing, and Testcontainers-based failure validation.
- **Delivery:** Kubernetes desired state with Kustomize overlays and an Argo CD pull-based GitOps flow using immutable image references and explicit rollout/rollback behavior.
- **Performance:** replacing an external Python embedding service with in-JVM embeddings and pgvector HNSW reduced a local serving benchmark from approximately **300–500 ms to 80–120 ms**.

`Java 21 · Spring Boot · Kafka · PostgreSQL · pgvector · Redis · Flyway · OpenTelemetry · Testcontainers · Docker · Kubernetes · Kustomize · Argo CD`

---

### [Kairos](https://github.com/Luca5Eckert/Kairos) — Graph-Augmented Retrieval Engine

A personal-knowledge backend that combines semantic retrieval with graph-based context expansion to retrieve evidence connected through passages, concepts, and extracted relationships.

- **Data ownership:** PostgreSQL/pgvector store durable sources, chunks, embeddings, triples, processing state, and retrieval history as the source of truth; Neo4j is a derived graph projection.
- **Retrieval:** dense passage recall, triple recall, graph seed selection, weighted Personalized PageRank, and ranking fusion support multi-hop context discovery.
- **AI pipeline:** `all-MiniLM-L6-v2` embeddings run locally on the JVM through ONNX Runtime; Gemini via Spring AI performs structured triple extraction and constrained graph-seed selection.
- **Reliability:** ingestion state is persisted before asynchronous enrichment, with explicit per-chunk progress and idempotent retry.
- **Infrastructure:** Terraform models an AWS development foundation including VPC, EC2/SSM, encrypted EBS, ECR, IAM boundaries, and remote S3 state.
- **Evaluation direction:** issue #110 defines a reproducible comparison of vector-only vs. graph/hybrid retrieval using Recall@K, MRR, NDCG@K, Precision@K, and latency.

`Java 21 · Spring Boot · Spring AI · ONNX Runtime · PostgreSQL · pgvector · Neo4j GDS · Gemini · Testcontainers · Terraform · AWS`

---

### [Portal Conecta](https://github.com/Portal-Conecta) — Multi-Service Academic Platform

A team platform in which a central backend owns identity, academic structure, permissions, integration contracts, and shared operational infrastructure.

I served as backend technical lead during the CentroWEG/SENAI final project, developed by more than 20 contributors across eight repositories and five services.

- **Service boundaries:** defined Hub Core as the source of truth for identity, academic structure, memberships, authentication, permissions, and contextual authorization.
- **Integration:** explicit OpenAPI contracts and RabbitMQ event flows connect the Hub Core with feature services.
- **Platform foundation:** owned the WebFlux API Gateway and shared operational infrastructure, including JWT validation, Redis-backed rate limiting, correlation IDs, W3C trace propagation, reusable MVC/WebFlux logging, and observability with Prometheus, Grafana, Loki, Tempo, and Alloy.

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

I am focused on backend and data-intensive systems where performance, explicit ownership, asynchronous integration, recoverability, and operational visibility matter.

My main areas of interest are distributed platforms, event-driven architectures, recommendation systems, retrieval infrastructure, data pipelines, system integration, and applied AI backends.
