# Kafka Learning Environment Checklist

> **Note:** Unless otherwise specified, all services/tools are intended to be run in Docker containers using docker-compose for local development. If a tool should be installed natively or as a managed service, it is explicitly stated below.

## 1. System Requirements (Check these first!)
- [x] Sufficient RAM (8GB+ recommended) — 16GB detected
- [x] Sufficient disk space (20GB+ free) — 14GB free (keep an eye on usage)
- [x] macOS version compatible with Docker, Minikube, etc. — macOS 12.7.6
- [x] Virtualization enabled (for Docker/Minikube) — Docker running

## 2. Core Tools (Must-have)
- [x] Docker & Docker Compose (native install)
  - [x] Docker version >= 20.x — 28.0.1
  - [x] Docker Compose version >= 1.29 — v2.33.1
- [x] Git (native install) — 2.37.1

## 3. Programming Languages
- [x] Python 3.8+ (native install) — 3.10.2
- [x] Java 11+ (native install) — 20.0.2
- [x] Node.js 18+ (native install) — 18.19.1

## 4. Orchestration
- [ ] Minikube or Kind (native install) — not installed
- [x] kubectl (native install) — v1.32.2 (from Docker Desktop)

## 5. Kafka Ecosystem
- [ ] Kafka (Docker)
- [ ] Kafka CLI tools (Docker)
- [ ] Kafka Connect (Docker)
- [ ] Kafka Streams (Java, native or Docker)
- [ ] ksqlDB (optional, Docker)

## 6. Monitoring & Analytics
- [ ] Prometheus (Docker)
- [ ] Grafana (Docker)
- [ ] Kafka Exporter (Docker)
- [ ] Elasticsearch & Kibana (optional, Docker)

## 7. Data Integration
- [ ] MongoDB (Docker or managed)

## 8. CI/CD
- [ ] GitHub Actions (cloud/managed)
- [ ] Jenkins (optional, Docker or native)

## 9. Managed Services
- [ ] Confluent Cloud account (cloud/managed)
- [ ] AWS account (for MSK/EKS/ECS) (cloud/managed)

## 10. Security
- [ ] SSL setup (later)
- [ ] SASL/ACLs (optional)

---

## Notes & Blockers
- Note any issues, blockers, or troubleshooting tips here.
