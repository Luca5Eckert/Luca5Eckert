# Lucas Eckert

Backend developer focused on **distributed JVM services**, **event-driven architecture**, and **retrieval/recommendation infrastructure**.

I build backend systems that separate what happened from what is served: durable write paths, event-built read models, vector search, graph traversal, and resilient APIs.

-> [Portfolio](https://lucas-eckert.vercel.app) · [LinkedIn](https://linkedin.com/in/lucas-ismael-eckert)

---

## current focus

- Building **VellumHub**, an event-driven recommendation platform using Kafka, PostgreSQL/pgvector, Redis, and Spring WebFlux.
- Building **Kairos**, a graph-augmented retrieval engine using local JVM embeddings, pgvector, Neo4j GDS, and Spring AI.
- Studying distributed systems and ML infrastructure through *Designing Data-Intensive Applications* and *Neural Networks and Deep Learning*.

---

## projects

### [VellumHub](https://github.com/Luca5Eckert/VellumHub)

Event-driven recommendation platform designed to serve personalized recommendations without query-time coupling to source-of-truth services.

The system uses Kafka events to build local read models across the book, rating, and user lifecycle. Recommendation queries are served from derived data instead of synchronously calling Catalog, Engagement, or User services at runtime.

**Core ideas**

- Event-Carried State Transfer over Kafka
- Event-built read models for recommendation queries
- Semantic candidate scoring with PostgreSQL/pgvector
- Cold-start profile seeding from onboarding preferences
- Reactive API Gateway with WebFlux, JWT validation, and Redis-backed rate limiting
- Retry topics and Dead Letter Topics for resilient asynchronous processing

**Stack**

`Java 21 · Spring Boot · Spring WebFlux · Kafka · PostgreSQL · pgvector · Redis · Docker`

---

### [Kairos](https://github.com/Luca5Eckert/Kairos)

Graph-augmented retrieval service that combines semantic search with graph traversal to retrieve context that pure vector similarity can miss.

Kairos ingests source material, persists chunks, generates local JVM embeddings, extracts factual triples through an LLM adapter, and builds both vector and graph indexes. Retrieval starts from semantic anchors in pgvector and expands through Neo4j Personalized PageRank for multi-hop context ranking.

**Core ideas**

- Durable ingestion pipeline before embedding and graph indexing
- Local ONNX embeddings running in-process on the JVM
- Triple extraction isolated behind a swappable Spring AI domain port
- Hybrid retrieval with pgvector semantic search and Neo4j graph traversal
- Graph-aware re-ranking with Neo4j GDS Personalized PageRank

**Stack**

`Java 21 · Spring Boot · Spring AI · PostgreSQL · pgvector · Neo4j · ONNX Runtime · Docker`

---

### [OpenIT](https://github.com/Luca5Eckert/OpenIt)

Reactive IoT access-control system connecting hardware events, payment flow, and real-time backend state propagation.

OpenIT bridges MQTT events from ESP32 hardware with a Spring WebFlux backend, allowing access state to be updated in real time without polling. The system also integrates payment flow with physical access grants.

**Core ideas**

- MQTT hardware event handling
- Reactive backend with Spring WebFlux
- Real-time access-state propagation with Server-Sent Events
- Payment integration tied to access control
- Frontend interface built with React and TypeScript

**Stack**

`Java 21 · Spring WebFlux · MySQL · MQTT · ESP32 · Node-RED · React · TypeScript`

---

## interests

- Distributed systems and event-driven architecture
- Event-built read models and eventual consistency
- Recommendation systems and cold-start strategies
- Retrieval engineering: vector search, graph-augmented search, and re-ranking
- Reactive APIs and resilience patterns
- Domain-driven design, hexagonal architecture, and clean service boundaries
- ML-informed backend infrastructure

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

**Platform and tooling**  
Docker · Docker Compose · GitHub Actions · Linux

---

## contact

- Portfolio: [lucas-eckert.vercel.app](https://lucas-eckert.vercel.app)
- LinkedIn: [linkedin.com/in/lucas-ismael-eckert](https://linkedin.com/in/lucas-ismael-eckert)
- Email: lucasismaeleckert@gmail.com
