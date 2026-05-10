# Lucas Eckert

I build backends that separate what happened from what is served — durable write paths, event-driven read models, and retrieval layers that follow meaning, not just word overlap.

→ [lucas-eckert.vercel.app](https://lucas-eckert.vercel.app/)

---

## now

Building **Kairos** — graph-augmented retrieval engine with durable ingestion, local ONNX embeddings on the JVM, LLM-based triple extraction via Spring AI, and multi-hop ranking with pgvector + Neo4j GDS.

Building **VellumHub** — event-fed recommendation platform with reactive gateway, ECST over Kafka, semantic embeddings, cold-start profile seeding, and retry/DLT resilience.

Reading *Designing Data-Intensive Applications* and *Neural Networks and Deep Learning* (Michael Nielsen) — working through the intersection of distributed systems and ML as it applies to backend infrastructure.

---

## interests

- Distributed systems and event-driven architecture
- Retrieval engineering — vector search, graph-augmented search, and re-ranking
- Recommender systems and cold-start strategies
- Reactive APIs and resilience patterns
- Domain-driven design and clean architecture
- How ML primitives — embeddings, gradients, attention — translate into backend design decisions

---

## projects

### [Kairos](https://github.com/Luca5Eckert/Kairos)

Retrieval engine that builds a knowledge graph from source material and uses it to surface context that pure vector search misses — connecting concepts across passages even when the exact same words never appear together.

**Why it matters:** most RAG pipelines stop at cosine similarity. Kairos adds graph-aware re-ranking with Personalized PageRank, allowing retrieval quality to improve as relationships between concepts accumulate.

- Dual ingestion flow with durable chunk persistence
- Local ONNX embeddings — in-process, JVM-native, no external inference service
- Triple extraction with Spring AI behind a clean domain port
- Graph-aware retrieval using Neo4j GDS Personalized PageRank

`Java 21 · Spring Boot 4 · Spring AI · PostgreSQL · pgvector · Neo4j · ONNX · Docker`

### [VellumHub](https://github.com/Luca5Eckert/VellumHub)

Recommendation platform designed to serve personalized results without query-time cross-service coupling.

**Design decision:** recommendation queries read from event-built models instead of coupling to source-of-truth services at runtime. Cold-start is handled at registration, not deferred to the first recommendation request.

- Reactive API Gateway with WebFlux, JWT auth, and Redis rate limiting
- Event-Carried State Transfer over Kafka — read models built from events, not joins
- 384-dim LangChain4j embeddings with L2 normalization for semantic candidate scoring
- Cold-start strategy seeded from explicit user preferences at registration
- Kafka retry topics and DLT for operational resilience without data loss

`Java 21 · Spring Boot · WebFlux · Kafka · PostgreSQL · pgvector · Redis · Docker`

### [OpenIT](https://github.com/Luca5Eckert/OpenIt)

IoT access control system that bridges hardware events with a reactive backend — MQTT device communication, real-time state propagation, and integrated payment flow.

- Reactive backend with WebFlux consuming MQTT events from physical hardware
- Real-time access state managed without polling
- Payment integration tied to physical access grants

`Java 21 · WebFlux · MQTT · React`

---

## stack

- **Languages & Frameworks:** Java 21 · Spring Boot · Spring WebFlux · Spring Security · Python · JavaScript
- **AI & Retrieval:** Spring AI · LangChain4j · ONNX Runtime · Neo4j GDS
- **Messaging & IoT:** Kafka · MQTT
- **Data:** PostgreSQL · pgvector · Neo4j · Redis · MySQL
- **Frontend:** React · Next.js · TypeScript
- **Platform:** Docker · Docker Compose
