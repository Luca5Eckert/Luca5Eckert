# Lucas Eckert

**Backend Software Developer · Java & Spring Boot · Distributed Systems**

I build backend services with **Java, Spring Boot and PostgreSQL**, focusing on how applications share data, enforce access rules and communicate across service boundaries.

[Portfolio & writing](https://lucas-eckert.vercel.app) · [LinkedIn](https://www.linkedin.com/in/lucas-ismael-eckert) · [Email](mailto:lucasismaeleckert@gmail.com)

## Engineering work

At **WEG**, I helped design, implement and deliver a shared **Java/Spring identity and authorization platform to production**, including its PostgreSQL-backed data foundation and web interface. I take responsibility for clear domain boundaries, reusable authentication contracts and a gradual transition away from legacy capabilities; the migration of every application and screen is still in progress.

I also developed engineering quality gates using real-PostgreSQL integration tests, ArchUnit architecture checks and CI/CD validation, so critical design decisions remain testable as services evolve.

I also built an **observability platform**: a Kubernetes/OpenTelemetry pipeline deployed in staging for a Java/Spring pilot, plus a Go backend and investigation interface that bring logs, metrics and traces together for service-level diagnosis.

## Selected projects

### [VellumHub](https://github.com/Luca5Eckert/VellumHub)
**Event-driven reading and recommendation platform**

I develop a platform where reading activity and preferences feed personalized recommendations. Kafka-fed local read models let recommendation queries work independently of upstream services, a behavior exercised in controlled integration tests. Transactional Outbox and idempotent consumers address publication and redelivery in selected flows; asynchronous projections introduce eventual consistency. Architecture fitness functions and distributed tests check the boundaries and failure behavior behind these decisions.

### [Kairos](https://github.com/Luca5Eckert/Kairos)
**Hybrid knowledge retrieval backend**

I develop a Java backend that retrieves knowledge using both semantic similarity and relationships between concepts. PostgreSQL/pgvector and Neo4j graph propagation support the two retrieval paths, compared through reproducible offline evaluation of ranking quality and query cost. Embeddings run locally inside the JVM with ONNX Runtime.

## How I work

I turn requirements into specifications and acceptance criteria, and review architectural trade-offs before implementation. I use Orca to orchestrate coding agents in Git worktrees, with versioned context and human review. CI quality gates provide feedback on changes; I remain responsible for reviewing the evidence and accepting the result.

Explore the project repositories for architecture and tests, or the [portfolio](https://lucas-eckert.vercel.app) for longer case studies and technical articles.

