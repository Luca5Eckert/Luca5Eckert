<div align="center">

# Lucas Ismael Eckert

**Desenvolvedor Backend Java | Spring Boot | Kafka | APIs REST | Microservices**

[![Email](https://img.shields.io/badge/Email-D14836?style=flat-square&logo=gmail&logoColor=white)](mailto:lucasismaeleckert@gmail.com)
[![GitHub](https://img.shields.io/badge/GitHub-181717?style=flat-square&logo=github&logoColor=white)](https://github.com/Luca5Eckert)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=flat-square&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/lucas-ismael-eckert-92a7bb399)

</div>

---

## Sobre

Engenheiro backend focado em construir sistemas escaláveis, confiáveis e simples de operar. Experiência prática com microsserviços orientados a eventos, engines de recomendação e aplicações baseadas em grafos usando Java e Spring Boot. Atua em ambiente profissional pelo programa de Aprendizagem Industrial na WEG, enquanto cursa Análise e Desenvolvimento de Sistemas.

---

## Experiência

**WEG S.A. — Desenvolvedor Backend (Programa de Aprendizagem Industrial)**  
Ago/2024 — Jul/2026 · Jaraguá do Sul, SC  
- Atuação como arquiteto de backend em projeto interno: definição de arquitetura REST com Spring Boot, modelagem de domínio e organização inspirada em Clean Architecture.  
- Estabelecimento de padrões de versionamento e revisão via pull requests, aumentando consistência e rastreabilidade do código.  
- Prática em ambiente ágil (Scrum/Kanban) com refinamentos técnicos, code reviews e CI/CD com GitHub Actions.

---

## Projetos em Destaque

### [VellumHub](https://github.com/Luca5Eckert/VellumHub)
Plataforma de recomendação de livros em arquitetura de microsserviços orientada a eventos.  
- Engine de recomendação em tempo real com **pgvector** e índice HNSW, reduzindo latência de ~300-500ms para **80-120ms**.  
- Streaming de mensagens via **Apache Kafka** para domínios independentes (user, catalog, engagement, recommendation); fetch em lote elimina N+1 e simplifica manutenção.  
`Java 21` `Spring Boot 3.4` `Apache Kafka` `PostgreSQL 15` `pgvector` `Docker Compose` `OpenFeign`

### [Vinculo](https://github.com/Luca5Eckert/Vinculo)
Rede social nativa em grafos com feed calculado por travessias Cypher.  
- Modelagem de 9 tipos de conexão ponderados (amizade, mentoria, colega) em **Neo4j**, permitindo consultas em sub-milissegundos.  
- Arquitetura Hexagonal e DDD com módulos independentes; pirâmide de testes 70-20-10 usando **Testcontainers**.  
`Java 21` `Spring Boot 4.0` `Neo4j 5` `JWT` `Spring Security` `Docker` `Virtual Threads`

### [Libera.ai](https://github.com/Luca5Eckert/Libera.ai)
Sistema IoT de controle de acesso e pagamentos para automação de cancelas.  
- Backend **Spring WebFlux** com SSE para notificação em tempo real; integração **Mercado Pago Checkout Pro** com webhook.  
- Clean Architecture e DDD em dois bounded contexts (access, payment); equipe de três com orquestração Node-RED e hardware ESP32 via MQTT.  
`Java 21` `Spring Boot 3.5` `React 19` `TypeScript` `MySQL` `MQTT` `Docker`

---

## Habilidades Técnicas

- **Linguagens:** Java (17/21), TypeScript, SQL, Python, C  
- **Backend:** Spring Boot, Spring WebFlux, REST APIs, SSE, Spring Security, JWT/OAuth2, JPA/Hibernate, OpenFeign  
- **Arquitetura:** Clean Architecture, Hexagonal, DDD, Microservices, Event-Driven Architecture  
- **Dados:** PostgreSQL, MySQL, Neo4j, pgvector, Apache Kafka, MQTT  
- **Testes & Qualidade:** JUnit 5, Mockito, Testcontainers, JaCoCo, pirâmide de testes 70-20-10, TDD  
- **Infraestrutura & Ferramentas:** Docker, Docker Compose, GitHub Actions (CI/CD), Node-RED, Git, Maven, OpenAPI/Swagger, Postman  
- **Frontend:** React, TypeScript, Vite, TailwindCSS  
- **Idiomas:** Português (Nativo), Inglês (Intermediário — B1/B2)

---

## Formação

- **CentroWEG / SENAI** — Desenvolvimento de Sistemas (Aprendizagem Industrial) · Ago/2024 — Jul/2026  
- **SESI** — Ensino Médio · Concluído

---

## Foco Atual

- 🎯 Projeto principal: evoluindo a plataforma **VellumHub** (event-driven, Kafka, pgvector, Docker)  
- 📚 Estudando: Clean Architecture, Domain-Driven Design, System Design e Graph Databases  
- 🔧 Praticando: arquitetura event-driven, princípios SOLID, Design Patterns e programação em C  
- 💡 Explorando: estruturas de dados, algoritmos e busca vetorial com pgvector
