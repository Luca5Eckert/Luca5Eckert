# Lucas Eckert

**Software Developer @ WEG · Java / Spring Boot · PostgreSQL · Distributed Systems**

I build backend systems where data access, state flow, integration boundaries, and measurable behavior matter. At WEG, I work on industrial software across performance, systems integration, legacy analysis, and domain evolution. Outside work, I use personal projects to go deeper into event-driven and data-intensive systems.

[Portfolio](https://lucas-eckert.vercel.app) · [LinkedIn](https://linkedin.com/in/lucas-ismael-eckert) · [Email](mailto:lucasismaeleckert@gmail.com)

---

## Selected systems

### [VellumHub](https://github.com/Luca5Eckert/VellumHub) — Event-Driven Recommendation Platform

A five-service Java/Spring backend that keeps recommendation serving local through Kafka-fed PostgreSQL/pgvector projections instead of request-time fan-out.

- Repeated reference runs stayed below **0.8 s p95** from interaction to visible ranking, with **260/260 interactions reflected**.
- After convergence, authenticated recommendation reads measured **16–20 ms p95**, and **60/60** succeeded with User, Catalog, and Engagement intentionally unavailable.

**Stack:** Java 21 · Spring Boot · Kafka · PostgreSQL · pgvector · Redis · Testcontainers · OpenTelemetry · Kubernetes

### [Kairos](https://github.com/Luca5Eckert/Kairos) — Graph-Augmented Retrieval Engine

A JVM-native retrieval engine that keeps PostgreSQL/pgvector as durable state and uses a rebuildable Neo4j GDS projection for graph propagation.

- In a controlled **60-query offline evaluation**, graph augmentation improved multi-hop **nDCG@10 from 0.65 to 0.96 (+47.6%)** over vector-only retrieval.
- The quality gain has an explicit cost: **418 ms graph p95 vs. 19 ms vector-only**, with a Docker-backed **12-query regression gate** protecting ranking quality in CI.

**Stack:** Java 21 · Spring Boot · ONNX Runtime · PostgreSQL · pgvector · Neo4j GDS · Personalized PageRank · Testcontainers

---

## Current interests

Java / JVM internals · distributed systems · PostgreSQL · event-driven architecture · reliability · retrieval evaluation

For deeper architecture notes, trade-offs, and professional work, see the [portfolio](https://lucas-eckert.vercel.app).
