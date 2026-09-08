# Lucas Eckert

**Software Developer @ WEG | Java/Spring Boot | PostgreSQL | Kafka**

Backend developer focused on performance, distributed systems, and data-intensive backend engineering.

I work in Industrial Software Engineering at WEG, building services and integrations where data modeling, reliability, system boundaries, and measurable performance matter. Outside work, I build event-driven recommendation infrastructure and graph-augmented retrieval systems with reproducible evaluation.

[Portfolio](https://lucas-eckert.vercel.app) · [LinkedIn](https://linkedin.com/in/lucas-ismael-eckert) · [Email](mailto:lucasismaeleckert@gmail.com)  
Jaraguá do Sul, Brazil · BRT / UTC-03 · English B2

---

## Professional work

I work at **WEG** as a **Software Developer** in **Industrial Software Engineering / Integrated Manufacturing Systems**, developing and integrating internal software used in manufacturing workflows.

Selected work includes:

- **Backend performance:** sequential/N+1-style relationship loading made organizational lookups expensive, so I moved hierarchical filtering into PostgreSQL and consolidated four core paths from **2 database queries to 1**; response time fell from **988 ms to 215 ms (-78%)** across a base of about **63K users**, with recurring warm-cache responses around **30 ms**.
- **Geolocation:** driver, mobile, and tracker position flows needed one backend boundary instead of separate integration paths, so I designed a **Java/Spring Boot** service with REST history/latest-position APIs, authenticated WebSocket telemetry, PostgreSQL, and Flyway; Testcontainers integration tests validate **3 critical boundaries** end to end: persistence, authentication, and tracker-message processing.
- **Checklist:** new audit inputs had to work consistently across editing, answering, persistence, PDF, and Excel flows, so I implemented Location and Organizational Structure capabilities across **NestJS/PostgreSQL, React/TypeScript, and FastAPI/Python**; targeted render/state changes also reduced interaction time on large forms from about **1.5 s to 45 ms**.
- **Engineering productivity:** three services had divergent local setup and validation paths, so I standardized them with Docker Compose and mandatory Jest/Vitest/Pytest gates before build/deployment; environment startup/setup fell from **5.5 to 2.26 minutes (-59%)**.

Previously, during the **CentroWEG/SENAI Industrial Apprenticeship Program**, I served as backend technical lead for **Portal Conecta**, a multi-service platform developed by more than 20 contributors across eight repositories and five services.

---

## Selected systems

### [VellumHub](https://github.com/Luca5Eckert/VellumHub) — Event-Driven Recommendation Platform

A five-service recommendation backend built around service-owned data, Kafka-fed local projections, and explicit eventual consistency.

- **Request-time fan-out would couple recommendation latency and availability to three upstream services**, so I moved cross-domain state through Kafka into Recommendation-owned PostgreSQL/pgvector projections; the local read path measured **15.98–19.86 ms p95**, and **60/60 authenticated reads succeeded** with User, Catalog, and Engagement intentionally unavailable.
- **Local projections introduce a consistency window after user interactions**, so I treated freshness as a measurable architecture budget and benchmarked the full `CreatedRatingEvent → Kafka → profile update → pgvector ranking → authenticated recommendation` path; two repeated 90-event reference runs stayed below **0.8 s p95 (553–751 ms)**, with **260/260 interactions reflected** and zero freshness failures.
- **The production-like 70/30 semantic+popularity ranker can trade relevance for popularity**, so I added a reproducible model-backed evaluation with MiniLM, pgvector, and controlled ablations over **120 books / 24 profiles**; it measured **nDCG@10 0.599 vs 0.066** for popularity-only, while semantic-only reached **1.000**, making popularity weighting the next tuning target rather than hiding the regression.

`Java 21 · Spring Boot · Kafka · PostgreSQL · pgvector · Redis · Flyway · OpenTelemetry · Testcontainers · Docker · Kubernetes · Kustomize · Argo CD`

---

### [Kairos](https://github.com/Luca5Eckert/Kairos) — Graph-Augmented Retrieval Engine

A JVM-native retrieval engine that combines dense retrieval with graph propagation for multi-hop evidence discovery.

- **Vector-only retrieval found relevant evidence but ranked multi-hop context less effectively**, so I use pgvector anchors to seed a user-scoped Neo4j Personalized PageRank projection; multi-hop **nDCG@10 improved from 0.65 to 0.96 (+47.6%)**, at the explicit cost of about **418 ms graph-augmented p95 vs 19 ms vector-only**, making GDS/PPR latency the next optimization target.
- **Treating both stores as authoritative would create dual-write and recovery ambiguity**, so PostgreSQL/pgvector remains the durable source of truth while Neo4j is a rebuildable derived projection; ingestion can recover from stored processing state without making graph availability part of durable ownership.
- **Retrieval changes can silently regress ranking quality**, so MiniLM embeddings run locally in the JVM and a Docker-backed **12-query regression gate** protects CI while a separate **60-query** benchmark measures quality and latency; evaluation stays reproducible without an external embedding-service dependency.

`Java 21 · Spring Boot · Spring AI · ONNX Runtime · PostgreSQL · pgvector · Neo4j GDS · Gemini · Testcontainers · Terraform · AWS`

---

### [Portal Conecta](https://github.com/Portal-Conecta) — Multi-Service Academic Platform

Backend technical leadership on an applied platform developed by **20+ contributors across 8 repositories and 5 services**.

- **Identity, academic structure, and authorization needed one authoritative boundary across multiple modules**, so I defined the Java/Spring Hub Core as the source of truth with explicit service boundaries and OpenAPI contracts; the architecture gave **20+ contributors across 8 repositories and 5 services** a common integration model instead of shared persistence.
- **Duplicating authentication and traffic concerns across services would increase coupling**, so I owned a Spring WebFlux API Gateway with JWT validation, Redis-backed rate limiting, correlation IDs, and W3C trace propagation; public ingress, security context, and request traceability were standardized at one edge.
- **Cross-service failures were difficult to diagnose without shared operational signals**, so I structured reusable logging and observability with Prometheus, Grafana, Loki, and Tempo; logs, metrics, and distributed traces became consistent across the platform instead of service-specific tooling.

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
