# Spring Boot + Kafka — 6-Day Intensive Roadmap

Stack: Java 21 (LTS) · Spring Boot 4.1.1 · Maven Wrapper · MySQL 8.0 · Apache Kafka (KRaft) · VS Code
Project: `learning-tracker` — grown incrementally across all six days.

---

## Day 1 — Modern Java + Spring Boot Foundations (Stage 1)

**Objectives:** explain what the Spring container actually does; wire beans three ways and justify
the choice; read an auto-configuration report and predict what Boot configured and why.

| # | Topic | Depth |
|---|-------|-------|
| 1.1 | Java refresh: records, sealed types, `var`, text blocks, switch patterns, Optional, Streams | fast — you know the base |
| 1.2 | Maven: POM anatomy, parent POM / BOM, dependency mediation, `mvnw`, lifecycle phases | medium |
| 1.3 | IoC & DI from first principles — why `new` in business code is a design flaw | deep |
| 1.4 | Bean lifecycle, scopes, `@Component` vs `@Bean`, constructor vs field injection, `@Qualifier`/`@Primary` | deep |
| 1.5 | `@SpringBootApplication` decomposed; component scanning; auto-configuration mechanism | deep |
| 1.6 | `application.properties`, `@Value`, `@ConfigurationProperties`, relaxed binding | medium |

**Task:** Tracker v1 — in-memory `DayProgress` store + a `/api/progress` read endpoint.
**Debug drills:** `NoSuchBeanDefinitionException`; two candidates for one type; circular dependency.
**Assessment:** A1 (10 questions, conceptual + predict-the-output).

---

## Day 2 — REST APIs & Backend Architecture (Stage 2)

**Objectives:** design a REST API you would defend in review; trace a request through the full
DispatcherServlet pipeline; handle every error path deliberately.

| # | Topic |
|---|-------|
| 2.1 | HTTP semantics: methods, idempotency, status codes, content negotiation |
| 2.2 | Request lifecycle: filter chain → DispatcherServlet → HandlerMapping → adapter → message converter |
| 2.3 | `@RestController`, `@RequestMapping` family, `@PathVariable` / `@RequestParam` / `@RequestBody` |
| 2.4 | Layering: controller / service / repository — and what belongs in each |
| 2.5 | DTOs vs entities, records as DTOs, mapping strategies |
| 2.6 | Bean Validation (`@Valid`, constraints, custom validators) |
| 2.7 | `@ControllerAdvice`, `@ExceptionHandler`, RFC 7807 ProblemDetail |
| 2.8 | API design: versioning, pagination, idempotency keys, HATEOAS (awareness only) |

**Task:** Tracker v2 — full CRUD, DTO layer, validation, centralized error handling.
**Debug drills:** 415 vs 400; silent `@Valid` no-op; lost exception translation.
**Assessment:** A2 + design critique of a deliberately bad API.

---

## Day 3 — Hibernate, JPA & MySQL (Stage 3)

**Objectives:** reason about the persistence context, not just annotations; diagnose N+1 from logs;
model relationships without the classic traps.

| # | Topic | Depth |
|---|-------|-------|
| 3.1 | ORM motivation; JPA spec vs Hibernate; `EntityManager` and the persistence context | deep |
| 3.2 | Entity states (new / managed / detached / removed), dirty checking, flush timing | deep |
| 3.3 | `@Entity`, `@Id` generation strategies, `@Column`, `@Embeddable` | medium |
| 3.4 | Relationships: `@OneToMany` / `@ManyToOne` / `@ManyToMany`, owning side, `mappedBy`, cascades | deep |
| 3.5 | **LAZY vs EAGER**, N+1 problem, `JOIN FETCH`, `@EntityGraph`, `LazyInitializationException` | deep |
| 3.6 | Spring Data JPA: derived queries, `@Query`, JPQL, projections, `Pageable` | medium |
| 3.7 | Transactions: `@Transactional`, propagation, isolation, the proxy self-invocation pitfall | deep |
| 3.8 | Schema management: `ddl-auto` is a dev shortcut — Flyway is production | medium |
| 3.9 | MySQL + Workbench: connection, inspecting generated SQL, `EXPLAIN`, indexing | medium |

**Task:** Tracker v3 — JPA entities on MySQL, `DayProgress` ↔ `Topic` ↔ `Exercise`, Flyway migrations.
**Debug drills:** N+1 reproduction and fix; `LazyInitializationException`; `@Transactional` self-call no-op.
**Assessment:** A3 + SQL-log reading exercise.

---

## Day 4 — Advanced Spring Boot: Security, Config, Testing (Stage 4)

**Objectives:** build a working JWT-authenticated API and explain each filter's job; write tests at
the right layer instead of booting the whole context every time.

| # | Topic |
|---|-------|
| 4.1 | Spring Security architecture: `SecurityFilterChain`, `AuthenticationManager`, `SecurityContext` |
| 4.2 | Authentication vs authorization; `UserDetailsService`; BCrypt and why not SHA-256 |
| 4.3 | Stateless JWT: structure, signing, validation, a custom auth filter, refresh-token tradeoffs |
| 4.4 | Method security with `@PreAuthorize`; role vs authority |
| 4.5 | Profiles, externalized config, secret handling, `@ConditionalOn*` |
| 4.6 | Logging: SLF4J / Logback, levels, structured logs, correlation IDs |
| 4.7 | Testing pyramid: plain unit, `@WebMvcTest`, `@DataJpaTest`, `@SpringBootTest`, Testcontainers |
| 4.8 | Actuator, metrics, the VS Code debugger, remote debug |

**Task:** Tracker v4 — JWT auth, role-gated endpoints, profiles, tests across all three layers.
**Debug drills:** 403 vs 401 diagnosis; filter ordering; CSRF on a stateless API; context-caching slowness.
**Assessment:** A4 + a security code review of a vulnerable controller.

---

## Day 5 — Apache Kafka (Stage 5)

**Objectives:** explain Kafka's storage and consumer-group model from first principles; pick and
justify a delivery semantic; build a producer/consumer pair with real error handling and a DLT.

| # | Topic | Depth |
|---|-------|-------|
| 5.1 | Why event-driven: coupling, backpressure, replay; log vs queue | deep |
| 5.2 | Architecture: brokers, KRaft (no ZooKeeper), topics, **partitions**, replication, ISR, leader election | deep |
| 5.3 | Offsets, commits (auto vs manual), retention, log compaction | deep |
| 5.4 | Producers: keys → partitioning, `acks`, `retries`, idempotence, batching | deep |
| 5.5 | Consumers: **consumer groups**, rebalancing, partition assignment, the poll loop, lag | deep |
| 5.6 | Serialization: JSON vs Avro, Schema Registry, schema evolution | medium |
| 5.7 | Delivery semantics: at-most-once / at-least-once / exactly-once; idempotent consumers | deep |
| 5.8 | Spring Kafka: `KafkaTemplate`, `@KafkaListener`, listener container factory, error handlers, retry, **dead-letter topics** | deep |
| 5.9 | Local Kafka via Docker Compose (KRaft) + CLI tools | medium |

**Task:** Tracker v5 — emit `progress.updated` events; a consumer builds a stats projection; DLT for poison messages.
**Debug drills:** consumer in wrong group sees nothing; deserialization poison pill; rebalance storm; ordering loss across partitions.
**Assessment:** A5 + partition-count and delivery-semantics design question.

---

## Day 6 — Integration & Professional Readiness (Stage 6)

**Objectives:** ship the whole thing coherently; defend your architecture; debug it unaided.

| # | Topic |
|---|-------|
| 6.1 | Architecture review: layering, transaction boundaries, Kafka-vs-DB consistency |
| 6.2 | Transactional outbox pattern (why dual-write is a bug) |
| 6.3 | Resilience: timeouts, retries, circuit breakers, graceful shutdown |
| 6.4 | Observability: health, metrics, tracing basics |
| 6.5 | Packaging and deployment: fat jar, layered Docker image, 12-factor config, CI sketch |
| 6.6 | Performance: connection pooling (HikariCP), query tuning, caching |
| 6.7 | Interview drill: system design + live debugging |

**Final:** Tracker v6 complete + capstone assignment + comprehensive assessment.

---

## Essential vs. Beyond-Six-Days

**Essential (covered properly):** DI/IoC, auto-configuration, REST + validation + error handling,
JPA persistence context, relationships, lazy loading, transactions, Spring Security + JWT, testing
layers, Kafka partitions / consumer groups / offsets / delivery semantics, Spring Kafka, DLTs.

**Awareness only — study further afterwards:** Avro + Schema Registry in depth, Kafka Streams and
ksqlDB, exactly-once transactional Kafka in production, the reactive stack (WebFlux, R2DBC),
Kubernetes, distributed tracing at scale, multi-datacenter replication, advanced JVM/GC tuning,
Spring Cloud.
