<div align="center">

# Lucas Eckert

**Desenvolvedor Backend Java** · Spring Boot · Kafka · Microserviços · Sistemas Distribuídos

[![Email](https://img.shields.io/badge/Email-D14836?style=flat-square&logo=gmail&logoColor=white)](mailto:lucasismaeleckert@gmail.com)
[![GitHub](https://img.shields.io/badge/GitHub-181717?style=flat-square&logo=github&logoColor=white)](https://github.com/Luca5Eckert)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=flat-square&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/lucas-ismael-eckert-92a7bb399)

</div>

---

## Sobre

Engenheiro backend focado em construir sistemas que sejam simples de operar, confiáveis em produção e fáceis de evoluir. Tenho experiência prática no desenvolvimento de APIs REST, microsserviços orientados a eventos e aplicações baseadas em grafos, com projetos que vão de plataformas de recomendação com busca vetorial a redes sociais nativas em grafos e sistemas IoT com pagamentos em tempo real.

Atualmente participando do Programa de Aprendizagem Industrial na **WEG S.A.**, atuando como arquiteto de backend em projeto interno do CentroWEG, enquanto curso Análise e Desenvolvimento de Sistemas.

Meu interesse principal está em como sistemas são projetados para escalar e permanecer manuteníveis: arquiteturas orientadas a eventos, design orientado a dados e as trocas reais envolvidas em sistemas distribuídos.

---

## Projetos em Destaque

### [VellumHub](https://github.com/Luca5Eckert/VellumHub)
Plataforma distribuída de recomendação de livros com catálogo comunitário, rastreamento de leitura e sugestões personalizadas via busca por similaridade vetorial. Construída com 4 microsserviços independentes, cada domínio (usuário, catálogo, engajamento, recomendação) separado e escalável de forma isolada.

O ponto central é a engine de recomendação em tempo real: perfis de usuário são representados como vetores e atualizados por eventos Kafka; a busca de livros similares usa pgvector com índice HNSW, reduzindo a latência de 300–500 ms para 80–120 ms em relação à abordagem anterior.

`Java 21` `Spring Boot` `Apache Kafka` `PostgreSQL` `pgvector` `OAuth2` `Docker Compose` `OpenFeign` `JUnit` `Mockito`

### [Vinculo](https://github.com/Luca5Eckert/Vinculo)
Rede social cujo modelo de dados é um grafo — não uma adaptação de banco relacional, mas uma aplicação construída do zero onde travessia de relacionamentos é operação de primeira classe. Utiliza Neo4j com 9 tipos de conexão ponderados (amizade, mentoria, colega de trabalho) e permite queries de grafo em sub-milissegundos mesmo em escala.

O feed personalizado é implementado como travessia Cypher: posts emergem com base na proximidade de conexão e na força do vínculo entre usuários, sem necessidade de serviço de recomendação separado. Arquitetura Hexagonal com 6 módulos independentes e pirâmide de testes 70-20-10 usando Testcontainers com instâncias reais do Neo4j.

`Java 21` `Spring Boot` `Neo4j` `Spring Security` `JWT` `Docker` `JUnit 5` `Testcontainers` `Hexagonal Architecture`

### [Libera.ai](https://github.com/Luca5Eckert/Libera.ai)
Sistema IoT completo para controle de acesso e pagamentos em estacionamentos. Sensores ESP32 detectam veículos e publicam eventos via MQTT; o backend Spring Boot processa o pagamento via Mercado Pago Checkout Pro e confirma a liberação da cancela sem intervenção humana.

A confirmação de pagamento é feita por webhook, e o status chega ao frontend instantaneamente via Server-Sent Events (WebFlux) — sem polling. Projeto em equipe de três pessoas: fui responsável pela camada de software completa (backend + frontend React/TypeScript); colegas cuidaram da orquestração Node-RED e integração do hardware.

`Java 21` `Spring Boot` `Spring WebFlux` `React 19` `TypeScript` `MySQL` `Mercado Pago SDK` `MQTT` `ESP32` `Docker`

### [SyncoApi](https://github.com/Luca5Eckert/SyncoApi)
API REST para gestão acadêmica com foco em qualidade: 152 testes e 68% de cobertura verificada via JaCoCo.

`Java 21` `Spring Boot` `Spring Security` `JWT` `MySQL` `Docker` `JaCoCo`

---

## Stack Técnica

<div align="center">

**Backend**

![Java](https://img.shields.io/badge/Java-ED8B00?style=flat-square&logo=openjdk&logoColor=white)
![Spring Boot](https://img.shields.io/badge/Spring_Boot-6DB33F?style=flat-square&logo=spring-boot&logoColor=white)
![Spring WebFlux](https://img.shields.io/badge/Spring_WebFlux-6DB33F?style=flat-square&logo=spring&logoColor=white)
![Apache Kafka](https://img.shields.io/badge/Apache_Kafka-231F20?style=flat-square&logo=apache-kafka&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![C](https://img.shields.io/badge/C-00599C?style=flat-square&logo=c&logoColor=white)

**Banco de Dados**

![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=flat-square&logo=mysql&logoColor=white)
![Neo4j](https://img.shields.io/badge/Neo4j-008CC1?style=flat-square&logo=neo4j&logoColor=white)

**Testes**

![JUnit 5](https://img.shields.io/badge/JUnit_5-25A162?style=flat-square&logo=junit5&logoColor=white)
![Mockito](https://img.shields.io/badge/Mockito-C5D9C8?style=flat-square&logoColor=black)
![Testcontainers](https://img.shields.io/badge/Testcontainers-291A3F?style=flat-square&logo=testcontainers&logoColor=white)

**DevOps & Ferramentas**

![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-2088FF?style=flat-square&logo=github-actions&logoColor=white)
![Git](https://img.shields.io/badge/Git-F05032?style=flat-square&logo=git&logoColor=white)

**Frontend**

![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white)
![React](https://img.shields.io/badge/React-61DAFB?style=flat-square&logo=react&logoColor=black)

</div>

---

## Foco Atual

- 🏗️ **Arquitetura:** Sistemas orientados a eventos, design orientado a dados e como bancos de dados influenciam a estrutura de um sistema
- 🔍 **Explorando:** Padrões de distribuição de dados, streaming de eventos e as trocas reais em sistemas distribuídos
- 🛠️ **Praticando:** Testcontainers, virtual threads do Java 21 e WebFlux para I/O reativo

---

## Estatísticas

<div align="center">

![GitHub Stats](https://github-readme-stats.vercel.app/api?username=Luca5Eckert&show_icons=true&hide_border=true&count_private=true&theme=default&hide=stars)

![GitHub Streak](https://github-readme-streak-stats.herokuapp.com/?user=Luca5Eckert&theme=default&hide_border=true&background=ffffff)

![Top Languages](https://github-readme-stats.vercel.app/api/top-langs/?username=Luca5Eckert&layout=compact&hide_border=true&theme=default&langs_count=6)

</div>

---

<div align="center">

![Profile Views](https://komarev.com/ghpvc/?username=Luca5Eckert&color=blue&style=flat-square&label=Visualizações)

</div>
