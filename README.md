# Lucas Eckert

**Backend Software Developer · Java / Spring Boot · Distributed Systems · Observability**

I design backend systems that can be **understood, verified, operated, and changed**. My core is Java/Spring and PostgreSQL; I work with distributed systems, messaging, data-intensive applications, and observability to make correctness and operational behavior visible.

Influenced by *Designing Data-Intensive Applications* and *A Philosophy of Software Design*, I try to reduce cognitive load, change amplification, and hidden coupling. Short feedback loops connect architecture decisions to tests, reproducible experiments, and telemetry; complexity is a cost to manage, not evidence of sophistication.

[Portfolio & technical writing](https://lucas-eckert.vercel.app) · [LinkedIn](https://linkedin.com/in/lucas-ismael-eckert) · [Email](mailto:lucasismaeleckert@gmail.com)

## Engineering approach

- **Keep systems understandable:** define explicit data ownership, useful abstractions, and boundaries that contain change rather than spread it. Prefer a modular monolith or distributed services based on real constraints, not fashion.
- **Make decisions testable:** encode important invariants with integration tests, Testcontainers, architecture fitness functions, and documented failure experiments. Iterate in small cycles that expose regressions early.
- **Observe before optimizing:** correlate structured logs, metrics, and distributed traces to infer internal behavior from external signals; use evidence of latency, errors, resource pressure, and event lag to justify a cache, query change, or reliability mechanism.
- **Report scope and uncertainty:** a CI pass is not a production rollout; a benchmark is not a service-level objective; instrumented does not necessarily mean end-to-end verified.

## Professional engineering

In professional industrial software engineering, I contribute to a cross-application observability platform using **OpenTelemetry/Collector, structured logs, Grafana, Loki, Tempo, Prometheus, MinIO, and a Go BFF** for correlated investigation. I support multiple applications and use service/JVM resource signals, errors, and traces to troubleshoot incidents, spot emerging memory pressure, and inform targeted optimizations or cache evaluation. I do not attribute a percentage reduction in detection time or memory use without a measured baseline. CI/CD also checks integration behavior and architectural boundaries with automated tests and fitness functions.


As a Software Developer, I work across requirements, architecture, Java/Spring Boot implementation, automated testing, integration, and delivery. I use PostgreSQL and a modular approach to domain boundaries; selected work includes contextual resource/action authorization with JWT RS256/JWKS and OAuth 2.0 Token Exchange patterns (backend implemented and tested; broader consumer integration pending), optimistic concurrency (ETag/If-Match, JPA/PostgreSQL revisions), Airflow/Dremio synchronization, and CI/CD with Docker/Kubernetes. One verified pipeline dropped from 4m09s to 3m05s (-25.7%) while retaining test and coverage gates.

Three scoped measurements on professional engineering paths:
- **630 → 60–70 ms (~89–90%)** for a hierarchical query path after reducing repeated data loads.
- **988 → 215 ms (~78%)** for a separate database-query path after query and filtering optimization.
- **1.5 s → 45 ms (~97%)** for a critical interaction in a large audit workflow, involving React, NestJS, and FastAPI.

These are scoped measurements rather than system-wide performance claims. Employer-owned project names, proprietary topology, confidential configuration and internal identifiers are not disclosed.

## Open engineering projects

### [VellumHub](https://github.com/Luca5Eckert/VellumHub) — Event-driven recommendation platform

**Problem:** Serving recommendations by querying multiple upstream services synchronously couples availability and latency to all of them.

**Decision:** Five Java/Spring services own their data and collaborate through Kafka domain facts. Recommendation materializes local PostgreSQL/pgvector read models for autonomous reads. Catalog keeps current reading progress canonical for read-your-write; Engagement receives history asynchronously.

**Evidence:** In controlled distributed runs, interaction-to-ranking freshness was **553–751 ms p95**, converged reads **15.98–19.86 ms p95**, and **60/60** reads completed with three upstream services unavailable. All **260/260** expected ranking signals were observed in the reference tests.

**Security and architecture:** Merged OAuth2/OIDC Authorization Server, Authorization Code + PKCE, Auth→User provisioning, verified Gateway token relay, RS256/JWKS validation, and architecture fitness functions in CI/CD for boundaries, event contracts, and recommendation read autonomy; final SPA/Google cutover remains separate.

**Observability:** A versioned local Grafana stack unifies **Micrometer/Prometheus metrics**, **structured JSON logs via Alloy/Loki**, and **OpenTelemetry traces via Alloy/Tempo**, with dashboards, alerts, and operational runbooks. End-to-end ingestion validation and instrumentation of the newer Auth service remain tracked gaps, not completed production claims. [Stack and validation scope](https://github.com/Luca5Eckert/VellumHub/blob/main/docs/OBSERVABILITY.md).

**Reliability:** Selected Catalog/Engagement Transactional Outbox streams merged in [#295](https://github.com/Luca5Eckert/VellumHub/pull/295), [#296](https://github.com/Luca5Eckert/VellumHub/pull/296) and [#297](https://github.com/Luca5Eckert/VellumHub/pull/297). [#299](https://github.com/Luca5Eckert/VellumHub/pull/299) then merged transactional consumer idempotency for canonical Book, Reading Progress, Rating and Reaction streams using durable event identities and revision checkpoints. Durable quarantine and ordered consumer recovery are implemented in [#301](https://github.com/Luca5Eckert/VellumHub/pull/301). Physical Kafka delivery remains at-least-once; merge does not establish coordinated production cutover, universal exactly-once semantics.

**Stack:** Java 21 · Spring Boot · Kafka · PostgreSQL/pgvector · Redis · Testcontainers

[Architecture, tests and trade-offs](https://github.com/Luca5Eckert/VellumHub) · [Transactional Outbox article](https://lucas-eckert.vercel.app/en/writing/transactional-outbox-tradeoffs)

### [Kairos](https://github.com/Luca5Eckert/Kairos) — Graph-augmented retrieval engine

**Problem:** Vector similarity can retrieve relevant passages while ranking multi-hop evidence poorly.

**Decision:** PostgreSQL/pgvector owns durable sources and retrieval history; Neo4j GDS is a derived graph projection. Local ONNX embeddings and weighted Personalized PageRank combine semantic anchors with relational propagation.

**Evidence:** In a controlled **60-query** offline evaluation, multi-hop **nDCG@10 increased from 0.6498 to 0.9593 (+47.6%)**; retrieval p95 also increased from **19.03 ms to 418.36 ms**. This is a measurable quality/latency trade-off, not a production SLA.

**Current limitation:** Reconciliation and full automated graph rebuild/fallback are not yet proven end to end; the system is experimental.

**Stack:** Java 21 · Spring Boot · PostgreSQL/pgvector · Neo4j GDS · ONNX Runtime

[Methodology and limitations](https://github.com/Luca5Eckert/Kairos/blob/main/docs/evaluation/retrieval-benchmark.md)

## Collaborative and complementary projects

**[Portal Conecta](https://github.com/Portal-Conecta/core-backend):** As a backend technical lead in a collaborative academic project, I worked on the [local Grafana/Prometheus/Loki/Tempo/Alloy observability stack](https://github.com/Portal-Conecta/observability), [Spring Cloud Gateway/WebFlux](https://github.com/Portal-Conecta/api-gateway), correlation IDs, trace propagation, and [reusable structured logging](https://github.com/Portal-Conecta/portal-logging). This is a documented local/academic implementation, not a claim of production monitoring.

**[Trama](https://github.com/Luca5Eckert/trama):** A Go/PostgreSQL modular monolith based on an atelier workflow, with explicit domain invariants and transactional writes.

## Technical interests

**Core:** Java/JVM · Spring Boot · PostgreSQL · domain and API design · concurrency · consistency · distributed systems

**Supporting:** Kafka · Redis · Testcontainers · Docker/Kubernetes · OpenTelemetry · graph/vector retrieval

My [portfolio](https://lucas-eckert.vercel.app) contains longer explanations and articles. All public architectural claims are tied to open projects; private employer implementation details remain private.
