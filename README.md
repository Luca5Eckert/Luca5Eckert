# Lucas Eckert

Backend developer focused on **JVM backend systems**, **event-driven architecture**, and **retrieval/recommendation infrastructure**.

I build backend systems around explicit state flow: durable write paths, event-built read models, vector search, graph traversal, and resilient APIs.

[Portfolio](https://lucas-eckert.vercel.app) · [LinkedIn](https://linkedin.com/in/lucas-ismael-eckert) · [Email](mailto:lucasismaeleckert@gmail.com)

---

## currently

- Building **VellumHub**, an event-driven recommendation platform with Kafka, PostgreSQL/pgvector, Redis, and Spring WebFlux.
- Building **Kairos**, a graph-augmented retrieval engine with local JVM embeddings, pgvector, Neo4j GDS, and Spring AI.
- Studying distributed systems, recommendation infrastructure, and ML fundamentals through *Designing Data-Intensive Applications* and *Neural Networks and Deep Learning*.

---

## selected systems

### [VellumHub](https://github.com/Luca5Eckert/VellumHub) · active

Event-driven recommendation platform designed to serve personalized recommendations without query-time coupling to source-of-truth services.

VellumHub uses Kafka events to build local read models across catalog, engagement, user, and recommendation boundaries. Recommendation queries are served from derived state instead of synchronously calling upstream services at runtime.

**What it proves**

- Event-Carried State Transfer over Kafka for local recommendation read models
- JVM-native semantic retrieval with PostgreSQL/pgvector and 384-dimensional embeddings
- Cold-start profile seeding from onboarding preferences
- Reactive API Gateway with WebFlux, JWT validation, and Redis-backed rate limiting
- Retry topics and Dead Letter Topics for resilient asynchronous processing
- Query-time serving from derived state instead of upstream service calls

**Stack**

`Java 21 · Spring Boot · Spring WebFlux · Kafka · PostgreSQL · pgvector · Redis · Docker`

---

### [Kairos](https://github.com/Luca5Eckert/Kairos) · active

Graph-augmented retrieval engine that combines semantic search with graph traversal to retrieve context that pure vector similarity can miss.

Kairos persists source material, chunks it durably, generates local JVM embeddings, extracts factual triples through an LLM adapter, and builds both vector and graph indexes. Retrieval starts from semantic anchors in pgvector and expands through Neo4j Personalized PageRank for multi-hop context ranking.

**What it proves**

- Durable ingestion before embedding and graph indexing
- Local ONNX embeddings running in-process on the JVM
- Triple extraction isolated behind a swappable Spring AI domain port
- Hybrid retrieval with pgvector semantic search and Neo4j graph traversal
- Graph-aware re-ranking with Neo4j GDS Personalized PageRank

**Stack**

`Java 21 · Spring Boot · Spring AI · PostgreSQL · pgvector · Neo4j · ONNX Runtime · Docker`

---

### [OpenIT](https://github.com/Luca5Eckert/OpenIt) · delivered

Reactive IoT access-control system where backend-confirmed payment state controls physical access.

OpenIT bridges MQTT events from ESP32 hardware with a Spring WebFlux backend, allowing access state to be updated in real time without polling. The system integrates payment flow with physical access grants and exposes live state updates to the frontend.

**What it proves**

- MQTT hardware event handling from ESP32 devices
- Reactive backend with Spring WebFlux
- Real-time access-state propagation with Server-Sent Events
- Payment flow tied to physical access control
- Frontend interface built with React and TypeScript

**Stack**

`Java 21 · Spring WebFlux · MySQL · MQTT · ESP32 · Node-RED · React · TypeScript`

---

## engineering focus

- Event-driven systems and event-built read models
- Retrieval engineering: vector search, graph traversal, and re-ranking
- Recommendation systems and cold-start strategies
- Reactive APIs, resilience patterns, and service boundaries
- Domain-driven design and hexagonal architecture

---

## stack

**Languages**  
Java · TypeScript · JavaScript · Python · SQL

**Backend**  
Spring Boot · Spring WebFlux · Spring Security · REST APIs · JWT · SSE

**Messaging and event-driven systems**  
Kafka · MQTT · Event-Carried State Transfer · Retry Topics · Dead Letter Topics

**AI, retrieval, and recommendation systems**  
Spring AI · LangChain4j · ONNX Runtime · Neo4j GDS · Vector Search · RAG

**Data stores**  
PostgreSQL · pgvector · Neo4j · Redis · MySQL

**Testing**  
JUnit 5 · Mockito · Testcontainers · Spring Boot Test

**Platform and tooling**  
Docker · Docker Compose · GitHub Actions · Linux

---

## contact

- Portfolio: [lucas-eckert.vercel.app](https://lucas-eckert.vercel.app)
- LinkedIn: [linkedin.com/in/lucas-ismael-eckert](https://linkedin.com/in/lucas-ismael-eckert)
- Email: [lucasismaeleckert@gmail.com](mailto:lucasismaeleckert@gmail.com)
