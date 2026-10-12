# Lucas Eckert

**Backend Software Developer · Java / Spring Boot · Software Engineering & Distributed Systems**

I design and build backend systems, from understanding the problem and existing constraints to architecture, implementation, integration, and delivery. My main stack is Java/Spring and PostgreSQL; distributed systems, data-intensive applications, and event-driven integration are areas of deeper work.

I aim for engineering proportional to the problem: sometimes a modular monolith is the right choice, sometimes independent services are. I document why, test the boundaries, and measure results rather than using architectural complexity as a credential.

[Portfolio](https://lucas-eckert.vercel.app) · [LinkedIn](https://linkedin.com/in/lucas-ismael-eckert) · [Email](mailto:lucasismaeleckert@gmail.com)

---

## How I approach engineering

- **Understand before building.** Investigate consumer needs, existing contracts, sources of data, and the reasons behind current behavior.
- **Choose the right boundaries.** Define domain ownership and favor simpler architecture until independent scaling, deployment, or failure isolation justifies complexity.
- **Deliver and verify.** Implement, integrate, test, and document changes; distinguish a working component, a deployed application, and actual adoption.

## Professional engineering

At **WEG**, I am a **Software Developer** in industrial software engineering. I take end-to-end technical responsibility for evolving a shared Java/Spring domain backend for applications in my section, from consumer discovery and architectural decisions through implementation, data synchronization, testing, and releases. I also contribute improvements to existing production systems developed by other teams.

The shared backend is being developed as a common reference for identity, organization, and access. I chose a **modular monolith with PostgreSQL** for closely related domains rather than distributing them prematurely. I implemented asymmetric **RS256/JWKS** identity verification for consumers, and designed an evolving authorization model where **feature availability in an organization is separate from user access granted through groups**. Feature-level grants and ecosystem-wide migration are not presented as complete.

Other representative outcomes:

- Improved a legacy organizational query from **988 ms to 215 ms (~78%)** in a documented comparison by eliminating sequential reads and filtering in the database.
- Reduced a critical interaction in a large audit form from approximately **1.5 s to 45 ms** through frontend state/rendering changes.
- Protected shared writes with conditional requests and PostgreSQL-aligned revisions, and established application release checks on the existing corporate deployment platform.

Those results refer to their specific measured scenarios, not system-wide production SLAs. My earlier geolocation contribution was an initial prototype, not ownership of the current deployed service.

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
