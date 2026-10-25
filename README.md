# Lucas Eckert

**Backend Software Developer · Java / Spring Boot · Distributed & Data-Intensive Systems**

I build and evolve backend services from problem discovery through design, implementation, testing, and delivery. Java/Spring and PostgreSQL are my core tools; distributed systems, event-driven integration, and data-intensive applications are where I develop deeper expertise.

Influenced by *Designing Data-Intensive Applications* and *A Philosophy of Software Design*, I favor clear ownership, manageable complexity, small verification cycles, and evidence-based trade-offs. Tests establish expected behavior; observability helps understand what happens when systems actually run.

[Portfolio & technical writing](https://lucas-eckert.vercel.app) · [LinkedIn](https://linkedin.com/in/lucas-ismael-eckert) · [Email](mailto:lucasismaeleckert@gmail.com)

## Engineering approach

- **Keep systems understandable:** define explicit data ownership, useful abstractions, and boundaries that contain change rather than spread it. Prefer a modular monolith or distributed services based on real constraints, not fashion.
- **Make decisions testable:** encode important invariants with integration tests, Testcontainers, architecture fitness functions, and documented failure experiments. Iterate in small cycles that expose regressions early.
- **Observe before optimizing:** correlate structured logs, metrics, and distributed traces to infer internal behavior from external signals; use evidence of latency, errors, resource pressure, and event lag to justify a cache, query change, or reliability mechanism.
- **Report scope and uncertainty:** a CI pass is not a production rollout; a benchmark is not a service-level objective; instrumented does not necessarily mean end-to-end verified.

## Professional engineering

As a Software Developer in industrial software engineering, I work across requirements, domain modeling, Java/Spring backend implementation, integration, automated tests, delivery, and support. My contributions include shared backend capabilities, PostgreSQL optimization, contextual authorization, optimistic concurrency across APIs and batch processing, and CI/CD verification.

I also develop **cross-application observability**: structured JSON events, W3C trace context, service/JVM metrics and correlated investigations through **OpenTelemetry/Collector, Grafana, Prometheus, Loki and Tempo**, with a **Go BFF** for the investigation interface. I use HTTP failures, latency and resource-pressure signals to support incidents and guide measured changes, while keeping identity context validated and telemetry labels low-cardinality. This is an operational engineering responsibility alongside backend design and delivery.

**Selected measured results:** a hierarchical query path improved from **630 to 60–70 ms**, a separate PostgreSQL lookup from **988 to 215 ms**, and a critical interaction in a large audit flow from **1.5 s to 45 ms**. These figures refer to their respective measured scenarios, not system-wide SLAs. I do not disclose employer-owned product names or proprietary details.

## Open engineering projects

### [VellumHub](https://github.com/Luca5Eckert/VellumHub) — Event-driven recommendation platform

**Problem:** Serving recommendations by querying multiple upstream services synchronously couples availability and latency to all of them.

**Decision:** Five Java/Spring services own their data and collaborate through Kafka domain facts. Recommendation materializes local PostgreSQL/pgvector read models for autonomous reads. Catalog keeps current reading progress canonical for read-your-write; Engagement receives history asynchronously.

**Evidence:** In controlled distributed runs, interaction-to-ranking freshness was **553–751 ms p95**, converged reads **15.98–19.86 ms p95**, and **60/60** reads completed with three upstream services unavailable. All **260/260** expected ranking signals were observed in the reference tests.

**Security and architecture:** OAuth2/OIDC with Authorization Code + PKCE, RS256/JWKS, identity provisioning, verified Gateway token relay, and architecture fitness functions protecting service boundaries and distributed behavior.

**Observability design:** The five Java/Spring application services export **Micrometer/Prometheus metrics**, **JSON container logs collected by Alloy into Loki**, and **OpenTelemetry Java Agent traces forwarded through Alloy to Tempo**. Grafana provides versioned HTTP, JVM/database, Kafka-flow and recommendation-health dashboards, alert rules and incident runbooks. Keeping the three collection paths distinct avoids duplicating metric/log export, while low-cardinality labels and log redaction control diagnostic cost and exposure. The local stack is configured; end-to-end collection verification and newer Auth instrumentation are tracked separately. [Architecture and runbooks](https://github.com/Luca5Eckert/VellumHub/blob/main/docs/OBSERVABILITY.md).

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

[Portal Conecta — backend engineering case study](case-studies/portal-conecta.md)

**[Trama](https://github.com/Luca5Eckert/trama):** A Go/PostgreSQL modular monolith based on an atelier workflow, with explicit domain invariants and transactional writes.

## Technical interests

**Core:** Java/JVM · Spring Boot · PostgreSQL · domain and API design · concurrency · consistency · distributed systems

**Supporting:** Kafka · Redis · Testcontainers · Docker/Kubernetes · OpenTelemetry · graph/vector retrieval

My [portfolio](https://lucas-eckert.vercel.app) contains longer explanations and articles. All public architectural claims are tied to open projects; private employer implementation details remain private.
