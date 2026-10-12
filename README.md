# Lucas Eckert

**Backend Software Developer · Java / Spring Boot · Distributed & Data-Intensive Systems**

I build and evolve backend systems with a focus on how data, state, and responsibilities cross service and persistence boundaries. My work covers APIs, domain modeling, event-driven integration, concurrency, and reliability.

I start with the problem and its constraints, choose explicit ownership and consistency rules, and validate the result through tests, measurements, and documented trade-offs. Complexity should solve a real problem—not become the goal.

[Portfolio](https://lucas-eckert.vercel.app) · [LinkedIn](https://linkedin.com/in/lucas-ismael-eckert) · [Email](mailto:lucasismaeleckert@gmail.com)

---

## Engineering approach

- **Boundaries before frameworks.** Decide which domain owns a fact, where it can change, and what other components actually need to know.
- **Correctness beyond the happy path.** Account for concurrent writes, stale state, partial failures, compatibility, and recovery.
- **Evidence over adjectives.** Compare alternatives with reproducible tests and benchmarks, report what improved, and name the cost.

## Professional engineering

At **WEG**, I work as a **Software Developer** on shared Java/Spring backend capabilities used by industrial applications. My work spans requirements discovery, domain and API design, organizational access rules, authentication, data synchronization, testing, and delivery.

Two examples of the engineering work:

- Protected writes across **seven mutable entities** with HTTP conditional requests (ETag/If-Match) and coordinated application/database revisions.
- Reduced organizational-tree response time from approximately **630 ms to 60–70 ms** in a documented measurement by pushing visibility filters into data access and constructing the response directly.

I also work on reconciling batch-imported data with application writes and evolving shared contracts without assuming every consumer can migrate at once. These are professional contributions within a team; the benchmark is not a production latency guarantee.

[Professional engineering cases](https://lucas-eckert.vercel.app/#professional-work)

## Selected systems

### [VellumHub](https://github.com/Luca5Eckert/VellumHub) — Event-Driven Recommendation Platform

**Problem:** Personalized recommendations need user, catalog, and engagement data, but reading that data synchronously from three upstream services would couple request latency and availability to all of them.

**Decision:** Five independently deployable Java/Spring services exchange domain facts through Kafka. Recommendation maintains PostgreSQL/pgvector read models locally, accepting bounded eventual consistency and duplicated state in exchange for autonomous reads.

**Evidence:** In controlled distributed reference runs, interaction-to-visible-ranking stayed below **0.8 s p95** with **260/260** expected updates reflected. After convergence, recommendation reads measured **16–20 ms p95**; **60/60** completed while User, Catalog, and Engagement were intentionally unavailable.

The project also explores event correctness: ordered transactional outbox delivery, versioned facts, durable consumer checkpoints, and idempotent projection effects for selected domain streams. Those changes are implemented and merged, **not claimed as production-validated**.

**Core:** Java 21 · Spring Boot · Kafka · PostgreSQL/pgvector · Redis · Testcontainers

[Architecture, trade-offs, benchmarks, and current guarantees](https://github.com/Luca5Eckert/VellumHub#architectural-trade-offs)

### [Kairos](https://github.com/Luca5Eckert/Kairos) — Graph-Augmented Retrieval Engine

**Problem:** Dense vector search can retrieve related passages yet fail to rank evidence that is connected across multiple pieces of knowledge.

**Decision:** Keep durable source content and history in PostgreSQL/pgvector, use Neo4j as a derived graph projection, and combine local ONNX embeddings with weighted Personalized PageRank. The external LLM handles relational interpretation rather than replacing the measurable retrieval core.

**Evidence:** In a **controlled 60-query offline evaluation**, graph augmentation improved multi-hop **nDCG@10 from 0.65 to 0.96 (+47.6%)**. It also increased p95 retrieval latency from **19 ms to 418 ms**, mostly in graph propagation. A **12-query CI quality gate** protects the ranking behavior.

Kairos is an **experimental retrieval backend**, not a production-ready or independently security-audited service.

**Core:** Java 21 · Spring Boot · ONNX Runtime · PostgreSQL/pgvector · Neo4j GDS · Testcontainers

[Evaluation methodology and limits](https://github.com/Luca5Eckert/Kairos/blob/main/docs/evaluation/retrieval-benchmark.md)

## Additional engineering work

- **[Portal Conecta](https://github.com/Portal-Conecta/core-backend) — Gateway & Observability:** Backend technical leadership in a collaborative platform developed during my industrial apprenticeship. I built much of the [observability stack](https://github.com/Portal-Conecta/observability) (OpenTelemetry tracing, Grafana, Prometheus, Loki, Tempo, Alloy and cross-service dashboards), developed the [Spring Cloud Gateway/WebFlux edge](https://github.com/Portal-Conecta/api-gateway) (JWT, Redis rate limiting, routing and trace propagation), and implemented shared [MVC/WebFlux structured logging](https://github.com/Portal-Conecta/portal-logging). I also contributed to the [Hub Core](https://github.com/Portal-Conecta/core-backend). This work was collaborative; the observability environment was implemented and documented locally, not verified as production monitoring.
- **[Trama](https://github.com/Luca5Eckert/trama):** A Go/PostgreSQL modular monolith shaped around the actual production workflow of a small atelier. Models color batches and ordered size runs explicitly, with transactional writes and architectural boundary tests.

## Technical focus

**Primary:** Java/JVM · Spring Boot · PostgreSQL · API and domain design · distributed systems · event-driven architecture · concurrency and consistency

**Supporting:** Kafka · Redis · Neo4j/pgvector · Testcontainers · Docker/Kubernetes · observability and CI/CD

Graph/vector retrieval and recommendation are areas where I apply these backend engineering principles, not a separate claim to an AI/ML engineering role.

For deeper implementation notes, verification scope, decisions, and trade-offs, see the **[portfolio](https://lucas-eckert.vercel.app)** and the linked project repositories.
