# Lucas Eckert

Backend Engineer focused on distributed systems, event-driven architecture, and retrieval infrastructure.
I build production-grade backends where data flow, resilience, and system boundaries are first-class design concerns.

Portfolio: [lucas-eckert.vercel.app](https://lucas-eckert.vercel.app/)

---

## Current focus

### [Kairos](https://github.com/Luca5Eckert/Kairos)
Graph-augmented retrieval engine that goes beyond vector similarity.

- Dual ingestion flow with durable chunk persistence
- Local ONNX embeddings on the JVM (no external embedding service)
- Triple extraction with Spring AI + Gemini behind a clean domain port
- Multi-hop retrieval with pgvector + Neo4j GDS (Personalized PageRank)
- Built with hexagonal architecture and clear domain boundaries

`Java 21 · Spring Boot 4 · Spring AI · PostgreSQL · pgvector · Neo4j · ONNX · Docker`

### [VellumHub](https://github.com/Luca5Eckert/VellumHub)
Backend reference platform for event-fed recommendations at scale.

- Reactive API Gateway (WebFlux) with JWT validation and Redis rate limiting
- Event-Carried State Transfer over Kafka for zero query-time coupling
- 384-dim semantic embeddings (LangChain4j) with L2 normalization
- Cold-start recommendation strategy seeded from user preferences
- Kafka retry topics + DLT for failure isolation and operational visibility

`Java 21 · Spring Boot · WebFlux · Kafka · PostgreSQL · pgvector · Redis · Docker`

---

## Project selection

### [OpenIT](https://github.com/Luca5Eckert/OpenIt)
IoT access-control and payment platform integrating hardware and reactive backend systems.

`Java 21 · WebFlux · MQTT · React`

---

## What I build

- Event-driven backends with strong read/write separation
- Resilient data pipelines with explicit failure handling
- Semantic and graph-enhanced retrieval systems
- Services designed for clarity, testability, and evolution

---

## Core stack

Java 21, Spring Boot, Spring WebFlux, Kafka, PostgreSQL, pgvector, Neo4j, Redis, Docker.
