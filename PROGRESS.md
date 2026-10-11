# Learning Tracker — Progress

Journey start: **2026-10-12** · Target completion: **2026-10-17**
Last updated: 2026-10-12

> This Markdown file is the **v0 tracker** — deliberately the simplest thing that works.
> From Day 1 onward the same data moves into the `learning-tracker` app: in-memory store (D1),
> REST + validation (D2), MySQL via JPA (D3), secured + tested (D4), Kafka-eventing (D5).
> Rule: a topic is marked **Done** only after demonstrated understanding or a completed task —
> never because it was explained.

Legend — Status: `Not started` / `In progress` / `Done`  ·  Confidence: 1 (shaky) … 5 (could teach it)

---

## Overall

| Stage | Module | Status | Progress |
|-------|--------|--------|----------|
| 0 | Environment setup | **Done** | 100% |
| 1 | Day 1 — Java + Spring Boot foundations | In progress | 0% |
| 2 | Day 2 — REST APIs & architecture | Not started | 0% |
| 3 | Day 3 — Hibernate, JPA & MySQL | Not started | 0% |
| 4 | Day 4 — Security, config & testing | Not started | 0% |
| 5 | Day 5 — Apache Kafka | Not started | 0% |
| 6 | Day 6 — Integration & readiness | Not started | 0% |

**Overall progress: 4%** (1 of 7 modules)

---

## Day 1 — Java + Spring Boot Foundations

| Topic | Status | Confidence | Needs revision |
|-------|--------|-----------|----------------|
| 1.1 Modern Java essentials | Not started | – | – |
| 1.2 Maven & build lifecycle | Not started | – | – |
| 1.3 IoC & dependency injection | Not started | – | – |
| 1.4 Beans: lifecycle, scopes, injection | Not started | – | – |
| 1.5 `@SpringBootApplication` & auto-configuration | Not started | – | – |
| 1.6 Externalized configuration | Not started | – | – |

Exercises: `0 / 3` · Coding task (Tracker v1): Not started · Assessment A1: not taken

---

## Days 2–6

All topics **Not started**. See `ROADMAP.md` for the full topic breakdown; rows are
copied into this file as each day begins.

---

## Assessment scores

| ID | Module | Score | Date |
|----|--------|-------|------|
| A1 | Day 1 | – | – |
| A2 | Day 2 | – | – |
| A3 | Day 3 | – | – |
| A4 | Day 4 | – | – |
| A5 | Day 5 | – | – |
| A6 | Day 6 (final) | – | – |

---

## Weak areas to revisit

_None recorded yet._

## Pending tasks

- [ ] Day 1 lessons 1.1–1.6
- [ ] Tracker v1 implementation
- [ ] Assessment A1
- [ ] Install Docker Desktop before Day 5 (needed for local Kafka)

---

## Environment (verified 2026-10-12)

| Component | Version / status |
|-----------|------------------|
| OS | Windows 11 Home Single Language 26300 |
| JDK | Oracle JDK 21.0.7 LTS — `C:\Program Files\Java\jdk-21` |
| `JAVA_HOME` | set (user scope) — **requires a new terminal to take effect** |
| Maven | via Maven Wrapper `mvnw` (no global install) |
| Git | 2.49.0 |
| VS Code | 1.140.0 |
| VS Code extensions | redhat.java, vscode-java-debug, vscode-java-test, vscode-java-dependency, vscode-maven, vmware.vscode-spring-boot, vscode-spring-boot-dashboard, vscode-spring-initializr |
| MySQL Server | 8.0 — service `MySQL80` **Running** |
| MySQL Workbench | 8.0 installed |
| MySQL CLI on PATH | **No** — pending (optional; Workbench is enough) |
| Docker (for Kafka) | **Not verified** — needed by Day 5 |
| Spring Boot | 4.1.1 — app builds, tests pass, `/actuator/health` returns UP |
