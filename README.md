# Lucas Eckert

Backend engineer focused on distributed systems, retrieval infrastructure, and event-driven architecture.

I build backends that separate what happened from what is served: durable write paths, event-driven read models, and retrieval layers that follow meaning, not just word overlap.

→ https://lucas-eckert.vercel.app  
→ https://linkedin.com/in/lucas-eckert

---

## now

Building **Kairos**: graph-augmented retrieval engine with durable ingestion, local ONNX embeddings on the JVM, LLM-based triple extraction via Spring AI, and multi-hop ranking with pgvector + Neo4j GDS.

Building **VellumHub**: event-fed recommendation platform with reactive gateway, Event-Carried State Transfer over Kafka, semantic embeddings, cold-start profile seeding, and retry/DLT resilience.

Reading *Designing Data-Intensive Applications* and *Neural Networks and Deep Learning* by Michael Nielsen — working through the intersection of distributed systems and ML as it applies to backend infrastructure.

---

## projects

### [Kairos](https://github.com/Luca5Eckert/Kairos)

Retrieval engine that builds a knowledge graph from source material and uses it to surface context that pure vector search misses — connecting concepts across passages even when the exact same words never appear together.

**Why it matters:** most RAG pipelines stop at cosine similarity. Kairos adds graph-aware re-ranking with Personalized PageRank, allowing retrieval quality to improve as relationships between concepts accumulate.

- Durable ingestion flow with persisted chunk pipeline before embedding generation
- Local ONNX embeddings running in-process on the JVM, with no external inference service
- Triple extraction with Spring AI isolated behind a clean domain port
- Graph-aware retrieval using Neo4j GDS Personalized PageRank
- Hybrid retrieval combining semantic similarity with graph traversal signals

`Java 21 · Spring Boot 4 · Spring AI · PostgreSQL · pgvector · Neo4j · ONNX Runtime · Docker`

---

### [VellumHub](https://github.com/Luca5Eckert/VellumHub)

Recommendation platform designed to serve personalized results without query-time cross-service coupling.

**Design decision:** recommendation queries read from event-built models instead of coupling to source-of-truth services at runtime. Cold-start is handled at registration, not deferred to the first recommendation request.

- Reactive API Gateway with WebFlux, JWT authentication, and Redis-backed rate limiting
- Event-Carried State Transfer over Kafka, with read models built from events instead of joins
- Semantic candidate scoring with vector embeddings and normalized similarity search
- Cold-start strategy seeded from explicit onboarding preferences
- Kafka retry topics and Dead Letter Topics for resilient asynchronous processing

`Java 21 · Spring Boot · WebFlux · Kafka · PostgreSQL · pgvector · Redis · Docker`

---

### [OpenIT](https://github.com/Luca5Eckert/OpenIt)

IoT access control system that bridges hardware events with a reactive backend — MQTT device communication, real-time state propagation, and integrated payment flow.

- Reactive backend with WebFlux consuming MQTT events from physical hardware
- Real-time access state managed without polling
- Payment integration tied to physical access grants

`Java 21 · Spring WebFlux · MQTT · React`

---

## interests

- Distributed systems and event-driven architecture
- Retrieval engineering: vector search, graph-augmented search, and re-ranking
- Recommender systems and cold-start strategies
- Reactive APIs and resilience patterns
- Domain-driven design and clean architecture
- ML-informed backend infrastructure

---

## stack

- **Languages:** Java · Python · TypeScript · JavaScript
- **Backend:** Spring Boot · Spring WebFlux · Spring Security
- **AI & Retrieval:** Spring AI · LangChain4j · ONNX Runtime · Neo4j GDS
- **Messaging:** Kafka · MQTT
- **Data:** PostgreSQL · pgvector · Neo4j · Redis · MySQL
- **Frontend:** React · Next.js
- **Platform:** Docker · AWS · Linux
