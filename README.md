# Lucas Eckert

**Backend Software Developer · Java & Spring Boot · Distributed Systems**

I design and develop backend software, from domain modeling and API contracts to implementation, integration and validation. My focus is on data consistency, service boundaries and making systems easier to evolve and diagnose.

[Portfolio & writing](https://lucas-eckert.vercel.app) · [LinkedIn](https://www.linkedin.com/in/lucas-ismael-eckert) · [Email](mailto:lucasismaeleckert@gmail.com)

## Engineering work

At **WEG**, I develop industrial backend software with **Java, Spring Boot and PostgreSQL**. My work includes a shared modular backend for identity and authorization, where domain boundaries and access contracts need to support integration across applications.

I also built an **observability platform**: a Kubernetes/OpenTelemetry pipeline deployed in staging for a Java/Spring pilot, plus a Go backend and investigation interface for logs, metrics and traces.

## Selected projects

### [VellumHub](https://github.com/Luca5Eckert/VellumHub)
**Event-driven reading and recommendation platform**

I use Kafka-fed local read models to serve recommendations independently of upstream services. Controlled integration tests exercise recommendation reads with those services unavailable. Transactional Outbox and idempotent consumers handle publication and redelivery in selected flows, while asynchronous projections introduce eventual consistency.

### [Kairos](https://github.com/Luca5Eckert/Kairos)
**Hybrid knowledge retrieval backend**

I combine PostgreSQL/pgvector with Neo4j graph propagation to investigate when relationships improve retrieval beyond semantic similarity. Offline evaluation compares ranking quality and query cost against vector-only retrieval. Embeddings run locally inside the JVM with ONNX Runtime.

## How I work

I turn requirements into explicit behavior and acceptance criteria, review architectural trade-offs and validate changes with integration tests, CI/CD and observability. I also use AI coding agents within this workflow, with versioned context, isolated Git worktrees and human review.

The [portfolio](https://lucas-eckert.vercel.app) contains the longer case studies and technical articles; each project repository documents its architecture, tests and engineering decisions.
