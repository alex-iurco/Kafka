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

## 3. Programming Languages & Tooling
- [x] Python 3.8+ (native install) — 3.10.2
- [x] Java 11+ (native install) — 20.0.2
  - [x] Maven (native install) — 3.9.9
  - [x] Gradle (native install) — 8.14
- [x] Node.js 18+ (native install) — 18.19.1

## 4. Orchestration
- [ ] Minikube (removed; using Google Cloud GKE instead)
- [x] kubectl (native install) — v1.32.2 (from Google Cloud SDK)
- [x] Google Cloud SDK (native install)
- [x] GKE Autopilot/Standard (cloud) — **Successfully deployed and tested**

## 5. Kafka Ecosystem
- [x] Kafka (GKE Autopilot, Helm/Bitnami) — **Running in cloud**
- [x] Kafka CLI tools (via client pod) — **Tested**
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
- [x] SASL/ACLs (Helm default, tested)

---

## Notes & Blockers
- GKE Autopilot cluster successfully created in us-central1 after troubleshooting regional resource and quota issues.
- Kafka and Zookeeper deployed using Bitnami Helm charts.
- PersistentVolumeClaim (PVC) affinity and GCP quota issues can cause pod scheduling failures; resolved by deleting and recreating PVCs in available zones.
- Kafka CLI client pod deployed and successfully produced/consumed messages with SASL/SCRAM authentication.
- Next: Implement Java/Python/Node.js producers and consumers as Kubernetes pods for microservices development.
