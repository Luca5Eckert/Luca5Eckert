# Lucas Eckert

Backend developer focused on distributed systems, event-driven architecture, and retrieval infrastructure.
I build production-grade backends with strong boundaries between write paths, read models, and serving layers.

Portfolio: [luca5eckert](https://lucas-eckert.vercel.app/)

---

## now

Building **Kairos** — graph-augmented retrieval engine with durable ingestion, local ONNX embeddings on the JVM, LLM-based triple extraction via Spring AI, and multi-hop ranking with pgvector + Neo4j GDS.

Building **VellumHub** — event-fed recommendation platform with reactive gateway, ECST over Kafka, semantic embeddings, cold-start profile seeding, and retry/DLT resilience.

---

## interests

- Distributed systems and event-driven architecture
- Retrieval engineering (vector + graph-augmented search)
- Recommender systems and cold-start strategies
- Reactive APIs and resilience patterns
- Domain-driven design and clean architecture

---

## projects

### [Kairos](https://github.com/Luca5Eckert/Kairos)
Personal knowledge graph retrieval engine designed to go beyond pure vector similarity.

- Dual ingestion flow with durable chunk persistence
- Local ONNX embeddings (in-process, JVM-native)
- Triple extraction with Spring AI behind a domain port
- Graph-aware retrieval using Neo4j GDS Personalized PageRank

`Java 21 · Spring Boot 4 · Spring AI · PostgreSQL · pgvector · Neo4j · ONNX · Docker`

### [VellumHub](https://github.com/Luca5Eckert/VellumHub)
Backend platform for recommendation serving without query-time cross-service coupling.

- Reactive API Gateway (WebFlux) with JWT and Redis rate limiting
- Event-Carried State Transfer over Kafka
- 384-dim LangChain4j embeddings with L2 normalization
- Cold-start strategy seeded from user preferences
- Kafka retry topics and DLT for operational resilience

`Java 21 · Spring Boot · WebFlux · Kafka · PostgreSQL · pgvector · Redis · Docker`

### [OpenIT](https://github.com/Luca5Eckert/OpenIt)
IoT access control and payment system integrating hardware events with a reactive backend.

`Java 21 · WebFlux · MQTT · React`

---

## core stack

- **Languages & Frameworks:** Java 21 · Spring Boot · Spring WebFlux · Spring Security · JWT · Python · JavaScript
- **AI & Retrieval:** Spring AI · LangChain4j · ONNX Runtime · Neo4j GDS
- **Messaging & IoT:** Kafka · MQTT · Node-RED
- **Data:** PostgreSQL · pgvector · Neo4j · Redis · MySQL
- **Frontend:** React · Next.js · TypeScript
- **Platform:** Docker · Docker Compose
