# Lucas Eckert

**Software Developer @ WEG | Java/Spring Boot | TypeScript/NestJS | PostgreSQL | Kafka | Distributed & Data-Intensive Systems**

Backend developer focused on Java/Spring Boot, performance, and data-intensive systems, with TypeScript/NestJS as a secondary backend stack.

I work in Industrial Software Engineering at WEG, building services and integrations where data modeling, reliability, system integration, and performance matter. Outside work, I build event-driven recommendation infrastructure and graph-augmented retrieval systems with reproducible evaluation.

[Portfolio](https://lucas-eckert.vercel.app) · [LinkedIn](https://linkedin.com/in/lucas-ismael-eckert) · [Email](mailto:lucasismaeleckert@gmail.com)  
Jaraguá do Sul, Brazil · BRT / UTC-03 · English B2

---

## Selected evidence

- **WEG — backend performance:** reduced an organizational lookup from **988 ms to 215 ms (-78%)** by removing sequential/N+1-style relationship loading and pushing hierarchical filtering into PostgreSQL. Four core lookup endpoints went from **2 database queries to 1** across about **63K users**; recurring warm-cache responses reached about **30 ms**.
- **Kairos — retrieval quality:** improved multi-hop **nDCG@10 from 0.65 to 0.96 (+47.6%)** over vector-only retrieval in a controlled **60-query offline evaluation** using production ONNX embeddings, PostgreSQL/pgvector, and Neo4j GDS Personalized PageRank. Recall@10 was already **1.00 in both modes**, so the result is a ranking-quality gain rather than a recall claim.
- **VellumHub — recommendation quality:** built a reproducible model-backed offline benchmark using the production MiniLM embedding path, pgvector, and **120 books / 24 profiles**. The current 70/30 semantic+popularity ranker reached **nDCG@10 0.599 vs 0.066** for popularity-only, while semantic-only reached **1.000**, exposing popularity weighting as the next tuning target rather than hiding the regression.
- **WEG — geolocation:** designed and implemented a **Java/Spring Boot** service for driver and vehicle tracking with REST APIs for position history/latest location, authenticated WebSocket telemetry ingestion, PostgreSQL, Flyway, and Testcontainers-backed integration testing.
- **WEG — engineering productivity:** standardized a three-service local environment with Docker Compose, reducing setup/startup from **5.5 to 2.26 minutes (-59%)**, and introduced automated test gates before build/deployment.

---

## Professional work

I work at **WEG** as a **Software Developer** in **Industrial Software Engineering / Integrated Manufacturing Systems**, developing and integrating internal software used in manufacturing workflows.

Selected work includes:

- optimizing organizational data access and database query patterns;
- designing a Java/Spring Boot geolocation boundary for REST and authenticated WebSocket telemetry;
- delivering Checklist capabilities across NestJS/PostgreSQL, React/TypeScript, and FastAPI/Python;
- designing persisted alert-delivery state with idempotency and retry-aware handling;
- improving local development and automated validation before application build/deployment.

Previously, during the **CentroWEG/SENAI Industrial Apprenticeship Program**, I served as backend technical lead for **Portal Conecta**, a multi-service platform developed by more than 20 contributors across eight repositories and five services.

---

## Selected systems

### [VellumHub](https://github.com/Luca5Eckert/VellumHub) — Event-Driven Recommendation Platform

A five-service backend shaped around service-owned persistence and Kafka-fed local read models so recommendation serving does not synchronously fan out to catalog, user, and engagement services.

- **Implemented:** service-owned databases, Kafka projections, pgvector/HNSW recommendation serving, gateway JWT enforcement, Redis-backed rate limiting, shared Kafka contracts, Flyway validation, retry/DLT infrastructure, and Kubernetes/Kustomize/Argo CD delivery definitions.
- **Performance:** moving recommendation retrieval from an external Python path to JVM-native ranking reduced a local benchmark from approximately **300–500 ms to 80–120 ms**.
- **Evaluation:** a reproducible offline harness runs the real `AllMiniLmL6V2EmbeddingModel` path, pgvector/Flyway/Testcontainers, and canonical ranking SQL across **120 books / 24 profiles**. The current 70/30 ranker measured **nDCG@10 0.599 vs 0.066** for popularity-only; semantic-only measured **1.000**, identifying the popularity term as a ranking-quality tuning target.
- **Evaluation boundary:** these are deterministic synthetic-text offline results, not an online A/B test or production SLA. The reference run records dataset seed/version, model/provider, commit SHA, ranking configuration, raw per-user results, and aggregate Precision/Recall/nDCG/MRR@10.
- **Current hardening:** transactional outbox, stronger consumer idempotency, production-security tightening, and broader distributed failure-path validation.

`Java 21 · Spring Boot · Kafka · PostgreSQL · pgvector · Redis · Flyway · OpenTelemetry · Testcontainers · Docker · Kubernetes · Kustomize · Argo CD`

---

### [Kairos](https://github.com/Luca5Eckert/Kairos) — Graph-Augmented Retrieval Engine

A JVM-native retrieval backend that combines semantic search with graph propagation to recover evidence connected through passages, concepts, and extracted relationships.

- **Measured retrieval quality:** multi-hop nDCG@10 improved from **0.65 to 0.96 (+47.6%)** over vector-only search in a controlled 60-query evaluation; overall nDCG@10 improved from about **0.82 to 0.98 (+18.8%)**.
- **Evaluation boundary:** production ONNX embeddings, real PostgreSQL/pgvector retrieval, and real Neo4j GDS/PPR; live Gemini recognition is intentionally excluded from the deterministic retrieval-core benchmark.
- **Continuous evaluation:** a Docker-backed **12-query regression gate runs in CI**, while the full 60-query quality/latency benchmark runs separately on demand and on schedule.
- **Trade-off:** graph-augmented p95 measured about **418 ms** versus **19 ms** for vector-only retrieval, with Neo4j GDS/PPR at about **401 ms p95**, making graph propagation the next optimization target.
- **Data ownership:** PostgreSQL/pgvector keep durable sources, chunks, embeddings, triples, processing state, and retrieval history; Neo4j is a rebuildable derived graph projection.
- **Local inference:** `all-MiniLM-L6-v2` embeddings run inside the JVM through ONNX Runtime, avoiding an external embedding service.

`Java 21 · Spring Boot · Spring AI · ONNX Runtime · PostgreSQL · pgvector · Neo4j GDS · Gemini · Testcontainers · Terraform · AWS`

---

### [Portal Conecta](https://github.com/Portal-Conecta) — Multi-Service Academic Platform

Backend technical leadership on an applied platform developed by **20+ contributors across 8 repositories and 5 services**.

- defined the Java/Spring Hub Core as the source of truth for identity, academic structure, permissions, and contextual authorization;
- designed service boundaries, persistence models, API contracts, and synchronous/asynchronous integration flows;
- owned the Spring WebFlux API Gateway with JWT validation, Redis-backed rate limiting, correlation IDs, and W3C trace propagation;
- structured shared logging and observability with Prometheus, Grafana, Loki, and Tempo.

---

## Technical stack

**Languages**  
Java · TypeScript · Python

**Frameworks**  
Spring Boot · Spring WebFlux · Spring Security · Spring Data JPA · NestJS

**Storage**  
PostgreSQL · Redis · Neo4j · pgvector

**Messaging**  
Apache Kafka · RabbitMQ

**Infrastructure**  
Docker · Kubernetes · AWS · Terraform · Kustomize · Argo CD

**Testing**  
JUnit 5 · Testcontainers · Jest · Vitest · Pytest

**Observability**  
OpenTelemetry · Prometheus · Grafana · Loki · Tempo

**Retrieval & AI**  
Spring AI · ONNX Runtime · HNSW · Neo4j GDS · Personalized PageRank

---

## Certifications

- Confluent Data Streaming Engineer — Foundations
- Apache Kafka Fundamentals Accreditation
- Neo4j Graph Data Science
- Neo4j and Generative AI
- Neo4j Fundamentals
- AWS Academy Cloud Foundations
- AWS Academy Generative AI Foundations
