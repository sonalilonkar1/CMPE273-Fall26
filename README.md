# CMPE273-Fall26
This repo is for course project for CMPE-273 Enterprise Distributed Systems for Fall-26

## CMPE 273 Project Ideas

Each team member has proposed one project idea. After reviewing and discussing all four ideas, the team will select one for the semester project.

---

## Idea 1: AgentOps – Multi-Agent Incident Diagnosis and Recovery

**Proposed by:** Sonali Lonkar

AgentOps is a multi-agent system that helps detect, diagnose, and recover from failures in distributed microservices applications. Since a request may travel through several services, identifying the actual cause of a failure can be difficult.

The system will use specialized AI agents for different responsibilities:

* A **Monitoring Agent** will detect unusual latency, error rates, and resource usage.
* A **Log Analysis Agent** will examine application logs.
* A **Trace Analysis Agent** will follow requests across multiple services.
* A **Root-Cause Agent** will combine the collected evidence to identify the likely problem.
* A **Recovery Agent** will recommend actions such as restarting, scaling, or isolating a service.
* A **Verification Agent** will check whether the problem was resolved.

Important or potentially risky recovery actions will require human approval.

The agents will run as separate containerized services and communicate using APIs and asynchronous messages. Possible technologies include LangGraph, MCP, Kafka, Docker, Kubernetes, OpenTelemetry, Prometheus, Grafana, and Jaeger.

The project will demonstrate distributed-systems concepts such as partial failures, fault isolation, timeouts, retries, circuit breakers, idempotency, asynchronous communication, scalability, and observability. We will test it by introducing service crashes, network delays, resource overload, duplicated messages, and agent failures.

---

## Idea 2: LedgerMesh – Distributed Transaction Coordination for a Rewards System

**Proposed by:** Shailen Sutradhar

LedgerMesh is a distributed rewards system that compares different approaches for maintaining transaction correctness across independent services. Redeeming points is not a single operation: the system must deduct points, reserve a reward, record the redemption, and ensure that every service reaches a consistent outcome even if part of the transaction fails.

The system will consist of several independent services:

* A **Redemption Coordinator** will manage the complete redemption workflow.

* A **Wallet Service** will maintain users’ points balances and process deductions and refunds.

* A **Rewards Catalog Service** will manage available rewards and inventory.

* An **Audit Ledger Service** will record redemption, failure, and compensation events.

The same redemption workflow will be implemented using two distributed transaction approaches:

* **Two-Phase Commit (2PC)** will ask every participating service to prepare the transaction before instructing all services to commit or abort.

* The **Saga Pattern** will complete a sequence of local transactions and execute compensating actions, such as refunding points or releasing a reserved reward, if a later step fails.

The services will run as separate containerized Python/FastAPI applications with independently owned data stores. They will communicate using APIs and asynchronous Kafka messages. OpenTelemetry traces, structured logs, and metrics will carry a common transaction ID across the services, allowing the team to observe each redemption and determine where and why it failed. Possible technologies include Python, FastAPI, Kafka, PostgreSQL, Docker, Kubernetes, OpenTelemetry, Prometheus, Grafana, and Jaeger.

The project will demonstrate distributed-systems concepts such as distributed transactions, consistency, partial failures, idempotency, asynchronous communication, retries, compensation, and observability. We will compare 2PC and Saga by introducing coordinator crashes, participant failures, timeouts, and duplicate or reordered messages, then measuring transaction correctness, availability, latency, blocking behavior, compensation frequency, and recovery time.

As a stretch goal, transaction-coordinator state could be stored in an etcd cluster to explore coordinator recovery and the consistency-versus-availability tradeoff during network partitions.

---

## Idea 3: Distributed API Rate Limiter
Project Idea

**Proposed by:** Shirisha Gujja

Modern applications often run multiple instances of the same API behind a load balancer. A rate limiter running independently inside each server cannot enforce a true global request limit because each server only knows about the requests it receives.

For example, if a user is limited to 100 requests per minute and requests are distributed across three API servers, independent rate limiters could collectively allow more than 100 requests.

This project will build a Distributed API Rate Limiter that enforces request limits consistently across multiple API server instances using shared distributed state.

**Core Features**

* A **Load Balancer** will route incoming traffic across multiple backend instances.

* Multiple **API Services** will process requests in parallel.

* A **Rate Limiting Service** will check whether a request should proceed or be throttled.

* **Redis** will keep the request-counting information shared across the system.

The rate limiter will use a **Token Bucket approach** so that each client receives a configurable request allowance over time. Limits can be applied using identifiers such as API keys, user IDs, or IP addresses. Requests beyond the allowed rate will be rejected with an HTTP 429 response.

Possible technologies include Python/FastAPI or Java/Spring Boot, Redis, NGINX, Docker, Kubernetes, Prometheus, Grafana.

The project will explore distributed-systems topics including concurrent access to shared state, coordination between multiple service instances, horizontal scaling, load balancing, fault handling, and monitoring. Testing will include high-concurrency traffic, scaling the number of API instances, and intentionally stopping services to observe whether rate limiting continues to behave correctly.

---

## Idea 4: Project Title

**Proposed by:** Team Member 4

*Add the project idea here.*
