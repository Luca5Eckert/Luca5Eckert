<div align="center">

# Lucas Ismael Eckert

Backend Java focado em sistemas distribuídos, microsserviços orientados a eventos e aplicações com boas práticas de arquitetura (Clean/Hexagonal, DDD). Trabalho com Spring Boot, Kafka, bancos relacionais e grafos, buscando soluções simples de operar, observáveis e fáceis de evoluir.

[![Email](https://img.shields.io/badge/Email-D14836?style=flat-square&logo=gmail&logoColor=white)](mailto:lucasismaeleckert@gmail.com)
[![GitHub](https://img.shields.io/badge/GitHub-181717?style=flat-square&logo=github&logoColor=white)](https://github.com/Luca5Eckert)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=flat-square&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/lucas-ismael-eckert-92a7bb399)

</div>

---

## Projetos em Destaque

### [VellumHub](https://github.com/Luca5Eckert/VellumHub)
Plataforma de recomendação de livros em microsserviços orientados a eventos.  
- Projetei a arquitetura distribuída e o fluxo de eventos em Kafka para isolar domínios (user, catalog, engagement, recommendation).  
- Implementei engine de recomendação em tempo real com **pgvector** (índice HNSW), reduzindo latência de ~300-500ms para **80-120ms**.  
- Redesenhei acesso a dados para remover N+1 com busca em lote e simplificar manutenção.  
`Java 21` `Spring Boot 3.4` `Apache Kafka` `PostgreSQL 15` `pgvector` `Docker Compose` `OpenFeign`

### [Vinculo](https://github.com/Luca5Eckert/Vinculo)
Rede social nativa em grafos com feed calculado por travessias Cypher.  
- Modelei 9 tipos de conexão ponderados em **Neo4j** para consultas de grafo sub-milissegundos.  
- Estruturei com Arquitetura Hexagonal/DDD e pirâmide de testes 70-20-10 usando **Testcontainers**.  
- Autenticação JWT stateless com RBAC e virtual threads para I/O concorrente.  
`Java 21` `Spring Boot 4.0` `Neo4j 5` `JWT` `Spring Security` `Docker` `Virtual Threads`

### [Libera.ai](https://github.com/Luca5Eckert/Libera.ai)
Sistema IoT de controle de acesso e pagamentos para automação de cancelas.  
- Desenvolvi backend **Spring WebFlux** com SSE para notificação em tempo real e integração **Mercado Pago Checkout Pro** via webhook.  
- Estruturei Clean Architecture em bounded contexts (access, payment), acoplando MQTT/ESP32 sem expor lógica de negócio.  
- Colaborei com equipe (Node-RED + hardware) para entregar fluxo fim a fim de pagamento e liberação de cancela.  
`Java 21` `Spring Boot 3.5` `React 19` `TypeScript` `MySQL` `MQTT` `Docker`

### [SyncoApi](https://github.com/Luca5Eckert/SyncoApi)
API REST acadêmica focada em centralizar comunicação e dados educacionais.  
- Organizei o projeto em camadas Clean Architecture com validações e serviços coesos.  
- Estruturei autenticação JWT, autorização por roles e testes (152 casos) com cobertura alta e pipelines de qualidade.  
`Java 21` `Spring Boot` `Spring Security` `JWT` `MySQL` `Docker` `JaCoCo`

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

## Foco Atual

- Projeto principal: evoluindo a plataforma **VellumHub** (event-driven, Kafka, pgvector, Docker)  
- Estudando: Clean Architecture, Domain-Driven Design, System Design e Graph Databases  
- Praticando: arquitetura event-driven, princípios SOLID, Design Patterns e programação em C  
- Explorando: estruturas de dados, algoritmos e busca vetorial com pgvector
