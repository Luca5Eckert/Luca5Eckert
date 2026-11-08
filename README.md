# Lucas Eckert

**Backend Software Developer · Java & Spring Boot · Distributed Systems**

I build backend services with **Java, Spring Boot and PostgreSQL**, focusing on how applications share data, enforce access rules and communicate across service boundaries.

[Portfolio & writing](https://lucas-eckert.vercel.app) · [LinkedIn](https://www.linkedin.com/in/lucas-ismael-eckert) · [Email](mailto:lucasismaeleckert@gmail.com)

## Engineering work

At **WEG**, I design and develop a shared modular backend for identity and authorization, giving applications reusable authentication contracts and organization-aware access rules.

I also built an **observability platform**: a Kubernetes/OpenTelemetry pipeline deployed in staging for a Java/Spring pilot, plus a Go backend and investigation interface that bring logs, metrics and traces together for service-level diagnosis.

## Selected projects

### [VellumHub](https://github.com/Luca5Eckert/VellumHub)
**Event-driven reading and recommendation platform**

I develop a platform where reading activity and preferences feed personalized recommendations. Kafka-fed local read models let recommendation queries work independently of upstream services, a behavior exercised in controlled integration tests. Transactional Outbox and idempotent consumers address publication and redelivery in selected flows; asynchronous projections introduce eventual consistency.

### [Kairos](https://github.com/Luca5Eckert/Kairos)
**Hybrid knowledge retrieval backend**

I develop a Java backend that retrieves knowledge using both semantic similarity and relationships between concepts. PostgreSQL/pgvector and Neo4j graph propagation support the two retrieval paths, compared through reproducible offline evaluation of ranking quality and query cost. Embeddings run locally inside the JVM with ONNX Runtime.

## How I work

I translate requirements into clear contracts and acceptance criteria, review architectural trade-offs and validate changes with integration tests and CI/CD. AI coding agents support this workflow through versioned context, Git worktrees and human review.

Explore the project repositories for architecture and tests, or the [portfolio](https://lucas-eckert.vercel.app) for longer case studies and technical articles.
