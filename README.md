# Lucas Eckert

**Backend Software Developer @ WEG · Java / Spring Boot · Distributed Systems · PostgreSQL · Kafka**

I build backend systems where data ownership, state transitions, integration boundaries, and measurable behavior matter. At WEG, I work across concurrency, performance, data synchronization, authentication, and production delivery. Outside work, VellumHub and Kairos are architecture laboratories: I document alternatives, accept/reject explicit consistency and reliability costs, and benchmark whether distributed state or graph retrieval complexity actually pays for itself.

[Portfolio](https://lucas-eckert.vercel.app) · [LinkedIn](https://linkedin.com/in/lucas-ismael-eckert) · [Email](mailto:lucasismaeleckert@gmail.com)

---

## Selected systems

### [VellumHub](https://github.com/Luca5Eckert/VellumHub) — Event-Driven Recommendation Platform

A five-service Java/Spring backend where domains deploy and scale independently, collaborate through Kafka facts, and materialize state where it is consumed. Recommendation accepts bounded eventual consistency for autonomous reads, while current reading progress stays canonical in Catalog to preserve read-your-write.

- Repeated reference runs stayed below **0.8 s p95** from interaction to visible ranking, with **260/260 interactions reflected**.
- After convergence, authenticated recommendation reads measured **16–20 ms p95**, and **60/60** succeeded with User, Catalog, and Engagement intentionally unavailable.

**Stack:** Java 21 · Spring Boot · Kafka · PostgreSQL · pgvector · Redis · Testcontainers · OpenTelemetry · Kubernetes

### [Kairos](https://github.com/Luca5Eckert/Kairos) — Graph-Augmented Retrieval Engine

A JVM-native retrieval engine that keeps relational authority in PostgreSQL/pgvector and uses Neo4j GDS as a derived graph projection. Local ONNX embeddings, external relational interpretation, recoverable chunk processing, and immutable answer snapshots make the boundaries explicit.

- In a controlled **60-query offline evaluation**, graph augmentation improved multi-hop **nDCG@10 from 0.65 to 0.96 (+47.6%)** over vector-only retrieval.
- The quality gain has an explicit cost: **418 ms graph p95 vs. 19 ms vector-only**, with a Docker-backed **12-query regression gate** protecting ranking quality in CI.

**Stack:** Java 21 · Spring Boot · ONNX Runtime · PostgreSQL · pgvector · Neo4j GDS · Personalized PageRank · Testcontainers

---

## Current interests

Java / JVM internals · distributed systems · PostgreSQL · event-driven architecture · reliability · retrieval evaluation

For deeper architecture notes, trade-offs, and professional work, see the [portfolio](https://lucas-eckert.vercel.app).
