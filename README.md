<div align="center">

# Hi 👋, I'm Hari Prasanth

<a href="https://git.io/typing-svg">
  <img src="https://readme-typing-svg.demolab.com?font=Fira+Code&weight=600&size=19&duration=3000&pause=1000&color=22D3EE&center=true&vCenter=true&width=720&lines=Associate+Software+Engineer;Java+(8%2F17%2F21)+%26+Spring+Boot+4+Specialist;Elasticsearch+Distributed+Search+%26+Inverted+Index;Observability+(Prometheus%2C+Grafana%2C+Zipkin);Microservices+%26+Cloud+(OpenFeign%2C+AWS);Scalability%2C+Load+Balancing+%26+Distributed+Caching;Fault+Tolerance+(Resilience4j)+%26+DB+Partitioning;Kafka+%26+RabbitMQ+Event-Driven+Architecture;System+Design+(HLD+%2F+LLD)+%26+MCP+AI+Work" alt="Typing SVG" />
</a>

<p align="center">
  <a href="mailto:hari.mba000@gmail.com">
    <img src="https://img.shields.io/badge/Email-hari.mba000%40gmail.com-blue?style=for-the-badge&logo=gmail&logoColor=white" alt="Email" />
  </a>
  <a href="https://github.com/hariprasanth-jcode">
    <img src="https://img.shields.io/badge/GitHub-hariprasanth--jcode-181717?style=for-the-badge&logo=github&logoColor=white" alt="GitHub" />
  </a>
</p>

<!-- Dynamic Animated Skill Icons Bar -->
<p align="center">
  <a href="https://skillicons.dev">
    <img src="https://skillicons.dev/icons?i=java,spring,postgres,redis,elasticsearch,kafka,rabbitmq,aws,docker,prometheus,grafana,maven,postman,idea,vscode,eclipse&theme=dark" alt="Dynamic Skill Icons" />
  </a>
</p>

---

</div>

### 👨‍💻 About Me

- 💼 **Role:** Associate Software Engineer
- ☕ **Core Expertise:** Enterprise backend systems with **Java (8 / 17 / 21)**, **Spring Boot (including Spring Boot 4)**, and **Microservices Architecture**.
- 📐 **System Design & Scalability:** Deep understanding of **High-Level Design (HLD)** and **Low-Level Design (LLD)**. Experienced with **Load Balancing** (NGINX, AWS ALB), **Horizontal & Vertical Scalability**, distributed **Caching** strategies (Redis), **Fault Tolerance Patterns** (Resilience4j Circuit Breaker, Rate Limiting, Bulkhead), and advanced **Database Design & Partitioning** (Sharding, Master-Slave Replication, Read Replicas).
- 🔍 **Distributed Search Engine (Elasticsearch):** Designing and implementing enterprise search with **Elasticsearch** — cluster architecture, primary/replica shards, inverted indexing, tokenizers/analyzers, and Spring Data Elasticsearch integration for sub-second full-text retrieval.
- 🔭 **Observability, Monitoring & Traceability:** Production-ready metrics and telemetry instrumentation with **Spring Boot Actuator** and **Micrometer**. Scraping and visualizing system metrics using **Prometheus** and **Grafana**, alongside distributed request tracing and latency analysis across microservices using **Zipkin**.
- 🧩 **Design Patterns:** Extensive hands-on with Gang of Four (GoF) patterns (*Creational, Structural, Behavioral*) and Distributed Systems patterns (*Saga, CQRS, Circuit Breaker, Outbox*).
- 🤖 **Agentic AI & MCP Work:** Building and integrating **Model Context Protocol (MCP)** tools and servers, enabling AI agents and LLMs to interact with enterprise databases, APIs, and microservices.
- ☁️ **Cloud & Containers:** Designing, deploying, and containerizing services with **AWS** & **Docker**.
- ⚙️ **Distributed Systems & Messaging:** Event-driven architecture with **Apache Kafka** & **RabbitMQ**, declarative inter-service REST communication with **Spring Cloud (OpenFeign)**, and **Saga Pattern (Choreography)**.
- ⚡ **Caching, Relational & Time-Series DBs:** High-performance caching with **Redis**, time-series data with **InfluxDB**, and relational/document persistence with **PostgreSQL**, MySQL, MongoDB, and Oracle.
- 🛡️ **Security & Cross-Cutting Concerns:** Aspect-Oriented Programming with **Spring AOP**, plus fine-grained authentication and authorization with **Spring Security** (JWT & Role/Permission control).
- 🔌 **Integration & Testing:** Robust **RESTful API Integration**, command-line HTTP testing with **cURL**, API automation with **Postman**, SMTP & email testing with **Mailpit**, payment gateways (Razorpay), and AI models (Hugging Face).
- 🧠 **Problem Solving:** Actively practicing **Data Structures & Algorithms (DSA)** in Java.

---

### 📐 System Architecture, Scalability & Observability

```mermaid
flowchart TD
    Clients([👥 Clients / Traffic]) --> LB[⚖️ Load Balancer<br/>NGINX / AWS ALB]
    
    subgraph MicroservicesTier ["🚀 Microservices Layer (Auto-Scaling & Resilience)"]
        direction LR
        S1["App Service A<br/>(Resilience4j & Feign)"]
        S2["App Service B<br/>(Spring Boot Actuator)"]
        S1 -->|Inter-Service Call<br/>with Trace/Span ID| S2
    end
    
    LB --> S1
    
    subgraph StorageTier ["🗄️ Caching, Partitioned Data & Search Tier"]
        direction LR
        Cache[(⚡ Redis Cache)]
        Primary[(Primary DB - Master)]
        Replica[(Read Replicas / Shards)]
        ES[(🔍 Elasticsearch Cluster<br/>Inverted Index & Shards)]
        Primary -->|Replication| Replica
        Primary -.->|Event Sync / CDC| ES
    end
    
    S1 <--> Cache
    S2 --> Primary
    S2 --> Replica
    S1 <-->|Full-Text Search & Analytics| ES

    subgraph ObservabilityTier ["🔭 Observability, Monitoring & Traceability Tier"]
        direction LR
        subgraph TracingSub ["Traceability"]
            Zipkin["📊 Zipkin Server<br/>(Distributed Tracing)"]
        end
        subgraph MonitoringSub ["Metrics & Monitoring"]
            Prometheus["🔥 Prometheus<br/>(Metrics Scraping)"]
            Grafana["📈 Grafana<br/>(Dashboards & Alerts)"]
            Prometheus --> Grafana
        end
    end

    S1 -.->|Trace Spans| Zipkin
    S2 -.->|Trace Spans| Zipkin
    S1 -.->|Metrics Scraping| Prometheus
    S2 -.->|Metrics Scraping| Prometheus
```

---

### 🔍 Elasticsearch Distributed Cluster Architecture

```mermaid
flowchart LR
    App([🚀 Microservice Client<br/>Spring Data Elasticsearch]) --> Coord[🧭 Coordinating Node<br/>Request Routing & Scatter-Gather]
    
    subgraph ESCluster ["🔍 Distributed Elasticsearch Cluster"]
        direction TB
        Master[👑 Master-Eligible Node<br/>Cluster State & Metadata]
        
        subgraph Node1 ["Data Node 1"]
            P0["Primary Shard 0<br/>(Inverted Index)"]
            R1["Replica Shard 1<br/>(Backup / Read Scale)"]
        end
        
        subgraph Node2 ["Data Node 2"]
            P1["Primary Shard 1<br/>(Inverted Index)"]
            R0["Replica Shard 0<br/>(Backup / Read Scale)"]
        end
    end
    
    Coord -->|Write / Query Routing| P0
    Coord -->|Write / Query Routing| P1
    Coord -.->|Read Load Balancing| R0
    Coord -.->|Read Load Balancing| R1
    Master -. Cluster Metadata .-> Node1
    Master -. Cluster Metadata .-> Node2
```

#### **Architecture, Scalability & Search Principles**

| Dimension | Strategy & Patterns | Tech & Implementations |
| :--- | :--- | :--- |
| **🔎 Distributed Search Engine** | Inverted Index, Sharding (Primary & Replica), Query-then-Fetch, Tokenization & Analyzers | Elasticsearch, Spring Data Elasticsearch |
| **📈 Scalability** | Horizontal & Vertical Scaling, Stateless Services, Asynchronous Pipelines | Docker, AWS, Kafka, Microservices |
| **⚖️ Load Balancing** | Round Robin, Least Connections, IP Hash, Layer 4 & Layer 7 Routing | NGINX, AWS ALB / ELB |
| **⚡ Caching Strategy** | Cache-Aside (Lazy Loading), Write-Through, Write-Back, TTL, LRU Eviction | Redis, Distributed Cache |
| **🛡️ Fault Tolerance** | Circuit Breaker, Bulkhead Isolation, Rate Limiting, Exponential Backoff, Fallback | Resilience4j, Spring Cloud |
| **🗄️ Database Design & Partitioning** | Horizontal & Vertical Sharding, Range/Hash Partitioning, Master-Slave Replication, Read Replicas, B-Tree Indexing | PostgreSQL, MySQL, InfluxDB |
| **📊 Monitoring & Metrics** | Real-time metric scraping, SLA/SLO tracking, threshold alerting, custom dashboards | Prometheus, Grafana, Spring Boot Actuator |
| **🔍 Traceability** | Distributed request tracing, Trace ID & Span ID propagation, latency bottleneck diagnosis | Zipkin, Micrometer Tracing |

<p align="left">
  <img src="https://img.shields.io/badge/Elasticsearch-Cluster_%26_Sharding-005571?style=for-the-badge&logo=elasticsearch&logoColor=white" alt="Elasticsearch" />
  <img src="https://img.shields.io/badge/Scalability-Horizontal_%26_Vertical-2E7D32?style=for-the-badge&logo=kubernetes&logoColor=white" alt="Scalability" />
  <img src="https://img.shields.io/badge/Load_Balancing-NGINX_%26_ALB-009688?style=for-the-badge&logo=nginx&logoColor=white" alt="Load Balancing" />
  <img src="https://img.shields.io/badge/Distributed_Caching-Redis-DC382D?style=for-the-badge&logo=redis&logoColor=white" alt="Caching" />
  <img src="https://img.shields.io/badge/Fault_Tolerance-Resilience4j-D32F2F?style=for-the-badge&logo=spring&logoColor=white" alt="Fault Tolerance" />
  <img src="https://img.shields.io/badge/Database_Partitioning-Sharding-0277BD?style=for-the-badge&logo=postgresql&logoColor=white" alt="Database Partitioning" />
  <img src="https://img.shields.io/badge/Monitoring-Prometheus_%26_Grafana-E6522C?style=for-the-badge&logo=prometheus&logoColor=white" alt="Monitoring" />
  <img src="https://img.shields.io/badge/Traceability-Zipkin-FF6F00?style=for-the-badge&logo=white" alt="Traceability" />
</p>

---

### 🛠️ Tech Stack & Skills

#### **Architecture, System Design & Design Patterns**
<p align="left">
  <img src="https://img.shields.io/badge/HLD_(High--Level_Design)-2E7D32?style=for-the-badge" alt="HLD" />
  <img src="https://img.shields.io/badge/LLD_(Low--Level_Design)-1565C0?style=for-the-badge" alt="LLD" />
  <img src="https://img.shields.io/badge/Design_Patterns-E040FB?style=for-the-badge" alt="Design Patterns" />
  <img src="https://img.shields.io/badge/Microservices_Architecture-326CE5?style=for-the-badge&logo=kubernetes&logoColor=white" alt="Microservices Architecture" />
  <img src="https://img.shields.io/badge/Model_Context_Protocol_(MCP)-8A2BE2?style=for-the-badge&logo=anthropic&logoColor=white" alt="MCP" />
  <img src="https://img.shields.io/badge/Saga_Pattern-Choreography-blueviolet?style=for-the-badge" alt="Saga Pattern" />
</p>

- 🏗️ **Creational Patterns:** Singleton, Factory Method, Abstract Factory, Builder, Prototype
- 🧩 **Structural Patterns:** Adapter, Decorator, Facade, Proxy, Composite
- 🔄 **Behavioral Patterns:** Observer, Strategy, Chain of Responsibility, Command, Template Method, State
- 🌐 **Enterprise & Distributed Patterns:** Saga Pattern (Choreography & Orchestration), CQRS, Circuit Breaker, Outbox Pattern, Event Sourcing

---

#### **Observability, Monitoring & Traceability**
<p align="left">
  <a href="https://prometheus.io/" target="_blank" rel="noreferrer">
    <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/prometheus/prometheus-original.svg" alt="Prometheus" width="44" height="44" title="Prometheus"/>
  </a>
  &nbsp;&nbsp;
  <a href="https://grafana.com/" target="_blank" rel="noreferrer">
    <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/grafana/grafana-original.svg" alt="Grafana" width="44" height="44" title="Grafana"/>
  </a>
  &nbsp;&nbsp;
  <a href="https://zipkin.io/" target="_blank" rel="noreferrer">
    <img src="https://img.shields.io/badge/Zipkin-Distributed_Tracing-FF6F00?style=for-the-badge&logoColor=white" alt="Zipkin" height="35" title="Zipkin Tracing"/>
  </a>
</p>
<p align="left">
  <img src="https://img.shields.io/badge/Prometheus-E6522C?style=for-the-badge&logo=prometheus&logoColor=white" alt="Prometheus" />
  <img src="https://img.shields.io/badge/Grafana-F46800?style=for-the-badge&logo=grafana&logoColor=white" alt="Grafana" />
  <img src="https://img.shields.io/badge/Zipkin-000000?style=for-the-badge&logoColor=white" alt="Zipkin" />
  <img src="https://img.shields.io/badge/Micrometer-Metrics_%26_Tracing-6DB33F?style=for-the-badge&logo=springboot&logoColor=white" alt="Micrometer" />
  <img src="https://img.shields.io/badge/Spring_Boot_Actuator-6DB33F?style=for-the-badge&logo=springboot&logoColor=white" alt="Spring Boot Actuator" />
</p>

---

#### **Languages**
<p align="left">
  <a href="https://www.oracle.com/java/" target="_blank" rel="noreferrer">
    <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/java/java-original.svg" alt="Java (8/17/21)" width="44" height="44" title="Java (8/17/21)"/>
  </a>
  &nbsp;&nbsp;
  <a href="https://en.wikipedia.org/wiki/SQL" target="_blank" rel="noreferrer">
    <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/postgresql/postgresql-original.svg" alt="SQL" width="44" height="44" title="SQL"/>
  </a>
</p>
<p align="left">
  <img src="https://img.shields.io/badge/Java_(8%2F17%2F21)-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white" alt="Java (8/17/21)" />
  <img src="https://img.shields.io/badge/SQL-4479A1?style=for-the-badge&logo=postgresql&logoColor=white" alt="SQL" />
</p>

#### **Backend & Microservices Ecosystem**
<p align="left">
  <a href="https://spring.io/projects/spring-boot" target="_blank" rel="noreferrer">
    <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/spring/spring-original.svg" alt="Spring Boot & Spring Boot 4" width="44" height="44" title="Spring Boot & Spring Boot 4"/>
  </a>
  &nbsp;&nbsp;
  <a href="https://spring.io/projects/spring-cloud" target="_blank" rel="noreferrer">
    <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/spring/spring-original-wordmark.svg" alt="Spring Cloud (OpenFeign)" width="44" height="44" title="Spring Cloud (OpenFeign)"/>
  </a>
  &nbsp;&nbsp;
  <a href="https://hibernate.org/" target="_blank" rel="noreferrer">
    <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/hibernate/hibernate-original.svg" alt="Hibernate & Spring Data JPA" width="44" height="44" title="Hibernate & Spring Data JPA"/>
  </a>
</p>
<p align="left">
  <img src="https://img.shields.io/badge/Spring_Boot-6DB33F?style=for-the-badge&logo=springboot&logoColor=white" alt="Spring Boot" />
  <img src="https://img.shields.io/badge/Spring_Boot_4-6DB33F?style=for-the-badge&logo=springboot&logoColor=white" alt="Spring Boot 4" />
  <img src="https://img.shields.io/badge/Spring_Cloud_(OpenFeign)-6DB33F?style=for-the-badge&logo=spring&logoColor=white" alt="Spring Cloud OpenFeign" />
  <img src="https://img.shields.io/badge/Spring_Security-6DB33F?style=for-the-badge&logo=springsecurity&logoColor=white" alt="Spring Security" />
  <img src="https://img.shields.io/badge/Spring_AOP-6DB33F?style=for-the-badge&logo=spring&logoColor=white" alt="Spring AOP" />
  <img src="https://img.shields.io/badge/Spring_Data_JPA-6DB33F?style=for-the-badge&logo=spring&logoColor=white" alt="Spring Data JPA" />
  <img src="https://img.shields.io/badge/Hibernate-59666C?style=for-the-badge&logo=hibernate&logoColor=white" alt="Hibernate" />
  <img src="https://img.shields.io/badge/RESTful_API_Integration-02569B?style=for-the-badge&logo=fastapi&logoColor=white" alt="RESTful API Integration" />
  <img src="https://img.shields.io/badge/JWT-000000?style=for-the-badge&logo=jsonwebtokens&logoColor=white" alt="JWT" />
</p>

#### **Messaging, Event Streaming & AI Agent Protocols**
<p align="left">
  <a href="https://kafka.apache.org/" target="_blank" rel="noreferrer">
    <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/apachekafka/apachekafka-original.svg" alt="Apache Kafka" width="44" height="44" title="Apache Kafka"/>
  </a>
  &nbsp;&nbsp;
  <a href="https://www.rabbitmq.com/" target="_blank" rel="noreferrer">
    <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/rabbitmq/rabbitmq-original.svg" alt="RabbitMQ" width="44" height="44" title="RabbitMQ"/>
  </a>
  &nbsp;&nbsp;
  <a href="https://activemq.apache.org/" target="_blank" rel="noreferrer">
    <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/apache/apache-original.svg" alt="ActiveMQ" width="44" height="44" title="ActiveMQ"/>
  </a>
</p>
<p align="left">
  <img src="https://img.shields.io/badge/Apache_Kafka-231F20?style=for-the-badge&logo=apachekafka&logoColor=white" alt="Kafka" />
  <img src="https://img.shields.io/badge/RabbitMQ-FF6600?style=for-the-badge&logo=rabbitmq&logoColor=white" alt="RabbitMQ" />
  <img src="https://img.shields.io/badge/ActiveMQ-D22128?style=for-the-badge&logo=apache&logoColor=white" alt="ActiveMQ" />
  <img src="https://img.shields.io/badge/Model_Context_Protocol_(MCP)-8A2BE2?style=for-the-badge&logo=anthropic&logoColor=white" alt="MCP" />
</p>

#### **Databases, Search Engines, Caching & Partitioning**
<p align="left">
  <a href="https://www.elastic.co/" target="_blank" rel="noreferrer">
    <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/elasticsearch/elasticsearch-original.svg" alt="Elasticsearch" width="44" height="44" title="Elasticsearch"/>
  </a>
  &nbsp;&nbsp;
  <a href="https://www.postgresql.org/" target="_blank" rel="noreferrer">
    <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/postgresql/postgresql-original.svg" alt="PostgreSQL" width="44" height="44" title="PostgreSQL"/>
  </a>
  &nbsp;&nbsp;
  <a href="https://redis.io/" target="_blank" rel="noreferrer">
    <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/redis/redis-original.svg" alt="Redis" width="44" height="44" title="Redis"/>
  </a>
  &nbsp;&nbsp;
  <a href="https://www.influxdata.com/" target="_blank" rel="noreferrer">
    <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/influxdb/influxdb-original.svg" alt="InfluxDB" width="44" height="44" title="InfluxDB"/>
  </a>
  &nbsp;&nbsp;
  <a href="https://www.mysql.com/" target="_blank" rel="noreferrer">
    <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/mysql/mysql-original.svg" alt="MySQL" width="44" height="44" title="MySQL"/>
  </a>
  &nbsp;&nbsp;
  <a href="https://www.mongodb.com/" target="_blank" rel="noreferrer">
    <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/mongodb/mongodb-original.svg" alt="MongoDB" width="44" height="44" title="MongoDB"/>
  </a>
  &nbsp;&nbsp;
  <a href="https://www.oracle.com/database/" target="_blank" rel="noreferrer">
    <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/oracle/oracle-original.svg" alt="Oracle" width="44" height="44" title="Oracle"/>
  </a>
</p>
<p align="left">
  <img src="https://img.shields.io/badge/Elasticsearch-005571?style=for-the-badge&logo=elasticsearch&logoColor=white" alt="Elasticsearch" />
  <img src="https://img.shields.io/badge/PostgreSQL-316192?style=for-the-badge&logo=postgresql&logoColor=white" alt="PostgreSQL" />
  <img src="https://img.shields.io/badge/Redis-DC382D?style=for-the-badge&logo=redis&logoColor=white" alt="Redis" />
  <img src="https://img.shields.io/badge/InfluxDB-22ADF6?style=for-the-badge&logo=influxdb&logoColor=white" alt="InfluxDB" />
  <img src="https://img.shields.io/badge/MySQL-4479A1?style=for-the-badge&logo=mysql&logoColor=white" alt="MySQL" />
  <img src="https://img.shields.io/badge/MongoDB-47A248?style=for-the-badge&logo=mongodb&logoColor=white" alt="MongoDB" />
  <img src="https://img.shields.io/badge/Oracle-F80000?style=for-the-badge&logo=oracle&logoColor=white" alt="Oracle" />
</p>

#### **Cloud, DevOps, Tools & Infrastructure**
<p align="left">
  <a href="https://aws.amazon.com/" target="_blank" rel="noreferrer">
    <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/amazonwebservices/amazonwebservices-original-wordmark.svg" alt="AWS" width="48" height="48" title="AWS"/>
  </a>
  &nbsp;&nbsp;
  <a href="https://www.docker.com/" target="_blank" rel="noreferrer">
    <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/docker/docker-original.svg" alt="Docker" width="44" height="44" title="Docker"/>
  </a>
  &nbsp;&nbsp;
  <a href="https://nginx.org/" target="_blank" rel="noreferrer">
    <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/nginx/nginx-original.svg" alt="NGINX" width="44" height="44" title="NGINX"/>
  </a>
  &nbsp;&nbsp;
  <a href="https://curl.se/" target="_blank" rel="noreferrer">
    <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/curl/curl-original.svg" alt="cURL" width="44" height="44" title="cURL"/>
  </a>
  &nbsp;&nbsp;
  <a href="https://git-scm.com/" target="_blank" rel="noreferrer">
    <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/git/git-original.svg" alt="Git" width="44" height="44" title="Git"/>
  </a>
  &nbsp;&nbsp;
  <a href="https://github.com/" target="_blank" rel="noreferrer">
    <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/github/github-original.svg" alt="GitHub" width="44" height="44" title="GitHub"/>
  </a>
  &nbsp;&nbsp;
  <a href="https://maven.apache.org/" target="_blank" rel="noreferrer">
    <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/maven/maven-original.svg" alt="Maven" width="44" height="44" title="Apache Maven"/>
  </a>
  &nbsp;&nbsp;
  <a href="https://www.postman.com/" target="_blank" rel="noreferrer">
    <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/postman/postman-original.svg" alt="Postman" width="44" height="44" title="Postman"/>
  </a>
  &nbsp;&nbsp;
  <a href="https://swagger.io/" target="_blank" rel="noreferrer">
    <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/swagger/swagger-original.svg" alt="Swagger" width="44" height="44" title="Swagger"/>
  </a>
  &nbsp;&nbsp;
  <a href="https://selenium.dev/" target="_blank" rel="noreferrer">
    <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/selenium/selenium-original.svg" alt="Selenium" width="44" height="44" title="Selenium"/>
  </a>
</p>
<p align="left">
  <img src="https://img.shields.io/badge/AWS-232F3E?style=for-the-badge&logo=amazonwebservices&logoColor=white" alt="AWS" />
  <img src="https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white" alt="Docker" />
  <img src="https://img.shields.io/badge/NGINX-009639?style=for-the-badge&logo=nginx&logoColor=white" alt="NGINX" />
  <img src="https://img.shields.io/badge/cURL-07354A?style=for-the-badge&logo=curl&logoColor=white" alt="cURL" />
  <img src="https://img.shields.io/badge/Mailpit-0052CC?style=for-the-badge&logo=minutemailer&logoColor=white" alt="Mailpit" />
  <img src="https://img.shields.io/badge/Git-F05032?style=for-the-badge&logo=git&logoColor=white" alt="Git" />
  <img src="https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white" alt="GitHub" />
  <img src="https://img.shields.io/badge/Apache_Maven-C71A36?style=for-the-badge&logo=apachemaven&logoColor=white" alt="Maven" />
  <img src="https://img.shields.io/badge/Postman-FF6C37?style=for-the-badge&logo=postman&logoColor=white" alt="Postman" />
  <img src="https://img.shields.io/badge/Swagger-85EA2D?style=for-the-badge&logo=swagger&logoColor=black" alt="Swagger" />
  <img src="https://img.shields.io/badge/Selenium-43B02A?style=for-the-badge&logo=selenium&logoColor=white" alt="Selenium" />
</p>

#### **IDEs & Environment**
<p align="left">
  <a href="https://www.jetbrains.com/idea/" target="_blank" rel="noreferrer">
    <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/intellij/intellij-original.svg" alt="IntelliJ IDEA" width="44" height="44" title="IntelliJ IDEA"/>
  </a>
  &nbsp;&nbsp;
  <a href="https://code.visualstudio.com/" target="_blank" rel="noreferrer">
    <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/vscode/vscode-original.svg" alt="VS Code" width="44" height="44" title="VS Code"/>
  </a>
  &nbsp;&nbsp;
  <a href="https://www.eclipse.org/" target="_blank" rel="noreferrer">
    <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/eclipse/eclipse-original.svg" alt="Eclipse" width="44" height="44" title="Eclipse"/>
  </a>
</p>
<p align="left">
  <img src="https://img.shields.io/badge/IntelliJ_IDEA-000000?style=for-the-badge&logo=intellijidea&logoColor=white" alt="IntelliJ IDEA" />
  <img src="https://img.shields.io/badge/VS_Code-007ACC?style=for-the-badge&logo=visualstudiocode&logoColor=white" alt="VS Code" />
  <img src="https://img.shields.io/badge/Eclipse-2C2255?style=for-the-badge&logo=eclipseide&logoColor=white" alt="Eclipse" />
</p>

---

### 🌟 Featured Highlights & Projects

- 🔄 **[Saga Pattern Choreography](https://github.com/hariprasanth-jcode/saga_pattern_choregraphy)** — Distributed transaction management across microservices using Spring Boot.
- ⚡ **[Spring Boot & Apache Kafka](https://github.com/hariprasanth-jcode/spring_boot_kafka)** — Event-driven architecture with asynchronous messaging and producer-consumer pipelines.
- 🛡️ **[Spring Security Role & Permissions](https://github.com/hariprasanth-jcode/spring_security_role_and_permission)** — Complete authentication and fine-grained authorization with JWT.
- 🤖 **[Spring Boot + Hugging Face AI](https://github.com/hariprasanth-jcode/spring_boot_hugging_face_ai)** — Integrating state-of-the-art AI models into Spring Boot backend services.
- 🐳 **[Dockerized Employee Service](https://github.com/hariprasanth-jcode/employee-service-docker)** — Containerized Spring Boot microservices ready for cloud deployment.
- 💳 **[Spring Boot Razorpay Integration](https://github.com/hariprasanth-jcode/springboot-razor-pay)** — End-to-end payment gateway processing.
