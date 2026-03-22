<div align="center">

# Lucas Eckert

Backend Developer — Java · Distributed Systems · Event-Driven Architecture

[![Email](https://img.shields.io/badge/Email-D14836?style=flat-square&logo=gmail&logoColor=white)](mailto:lucasismaeleckert@gmail.com)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=flat-square&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/lucas-ismael-eckert-92a7bb399)

</div>

---

### Sobre

Desenvolvedor backend com foco em Java e sistemas distribuídos.
Tenho interesse genuíno nas decisões que os tutoriais ignoram — consistência eventual, modelo de dados como arquitetura, trade-offs reais em sistemas sob pressão.

Atualmente na **WEG S.A.** como aprendiz industrial (CentroWEG/SENAI), trabalhando em projetos reais com equipe, Scrum e entregas formais.

---

### Interesses

- Sistemas distribuídos e arquitetura orientada a eventos
- Cruzamento entre ML e backend — embeddings na JVM, busca vetorial
- Algoritmos e estruturas de dados
- Lendo agora: *Designing Data-Intensive Applications* — Kleppmann

---

### Projetos

**[VellumHub](https://github.com/Luca5Eckert/VellumHub)** — recomendação de livros com microsserviços e busca vetorial
- Engine evoluiu de serviço Python externo (~300ms) para embeddings na JVM com LangChain4j + pgvector (~80ms)
- 4 microsserviços comunicando via Kafka com padrão ECST para sync assíncrono de estado

`Java 21` `Spring Boot` `Kafka` `pgvector` `LangChain4j` `Docker`

---

**[Vinculo](https://github.com/Luca5Eckert/Vinculo)** — rede social nativa em grafos
- Feed implementado como travessia Cypher pelo grafo — sem serviço de recomendação separado
- Conexões como state machine (PENDING → ACCEPTED/REJECTED) via Strategy pattern; 9 tipos ponderados

`Java 21` `Spring Boot` `Neo4j` `Hexagonal Architecture` `Testcontainers` `Virtual Threads`

---

**[OpenIT](https://github.com/Luca5Eckert/OpenIt)** — controle de acesso IoT com pagamento integrado
- Dois bounded contexts DDD (acesso + pagamento), ESP32 via MQTT, tempo real com SSE/WebFlux
- Projeto multidisciplinar apresentado formalmente para supervisores da WEG/SENAI

`Java 21` `Spring WebFlux` `React 19` `TypeScript` `DDD` `MQTT` `Mercado Pago`

---

<div align="center">

![GitHub Streak](https://streak-stats.demolab.com/?user=Luca5Eckert&theme=default&hide_border=true&background=00000000)

</div>
