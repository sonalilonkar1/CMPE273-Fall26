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

## Idea 2: Project Title

**Proposed by:** Team Member 2

*Add the project idea here.*

---

## Idea 3: Project Title

**Proposed by:** Team Member 3

*Add the project idea here.*

---

## Idea 4: Project Title

**Proposed by:** Team Member 4

*Add the project idea here.*
