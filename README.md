# Lucas Eckert

Backend developer focused on Java/Spring systems, event-driven integration, observability, and explicit ownership of state.

[Portfolio](https://lucas-eckert.vercel.app) · [LinkedIn](https://www.linkedin.com/in/lucas-ismael-eckert) · [Email](mailto:lucasismaeleckert@gmail.com)

## Current work

I am part of the WEG/CentroWEG-SENAI Systems Development Apprenticeship Program, combining technical coursework with applied team-based software delivery.

My main backend scope is **Portal Conecta**, where I work across Hub Core boundaries, authorization, API contracts, administrative imports, messaging, gateway behavior, reusable logging, and observability.

## Selected work

### [Portal Conecta](https://github.com/Portal-Conecta)

Central backend for shared identity, academic structure, permissions, and integration contracts in a modular academic platform.

Individual evidence: [CSV/XLSX user import](https://github.com/Portal-Conecta/core-backend/pull/293) and [CSV/XLSX class import](https://github.com/Portal-Conecta/core-backend/pull/296), both with dry-run validation and explicit conflict policies. A Hub Core release was validated by **682 Maven tests with no failures or errors**; this is a team-system result.

### [VellumHub](https://github.com/Luca5Eckert/VellumHub)

Event-driven recommendation backend that serves from Kafka-fed PostgreSQL/pgvector read models instead of synchronously calling upstream services. Replacing a Python sidecar with in-process JVM embeddings reduced a local benchmark from approximately **300–500 ms to 80–120 ms**; latest consolidated validation: **478 Maven tests passing**.

### [Kairos](https://github.com/Luca5Eckert/Kairos)

JVM-native graph-augmented retrieval backend combining ONNX embeddings, PostgreSQL/pgvector, Gemini triple extraction, and Neo4j GDS. Latest local verification: **244 tests executed**, **86.77% line coverage**, and **74.54% branch coverage**.

### [OpenIt](https://github.com/Luca5Eckert/OpenIt)

IoT access-control and payment flow where the backend persists Mercado Pago confirmation before sending a gate command through Node-RED, MQTT, and ESP32.

## Core stack

Java 17/21 · Spring Boot · Spring Security · Kafka · RabbitMQ · PostgreSQL · pgvector · Neo4j · Redis · Docker · JUnit · Testcontainers · OpenTelemetry · Prometheus · Grafana

## Direction

Seeking junior backend and software engineering roles involving Java, APIs, messaging, data modeling, testing, distributed-system boundaries, and operational visibility.
