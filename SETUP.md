# Kafka Learning Environment Setup

This document outlines all the tools, frameworks, and services required for your Kafka mastery journey, along with installation and setup notes for each. Use this as a checklist and reference as you build out your learning environment.

---

## 1. Core Tools
- **Docker & Docker Compose**: For running Kafka, Zookeeper, MongoDB, and supporting services locally.
- **Git**: For version control and collaboration.

## 2. Programming Languages & Frameworks
- **Python**: For producers/consumers and microservices (FastAPI)
- **Java**: For producers/consumers, Kafka Streams, and microservices (Spring Boot)
- **Node.js**: For producers/consumers and microservices (Express)

## 3. Kafka Ecosystem
- **Apache Kafka**: Core messaging platform (local via Docker, managed via Confluent Cloud/AWS MSK)
- **Kafka Connect**: For integrating with MongoDB and other data sources/sinks
- **Kafka Streams**: For stream processing (Java)
- **ksqlDB**: Optional, for SQL-like stream processing

## 4. Orchestration
- **Kubernetes**: For orchestrating multi-service deployments
  - **Minikube** or **Kind**: Lightweight local Kubernetes clusters
  - **kubectl**: Kubernetes command-line tool

## 5. Monitoring & Analytics
- **Prometheus**: Metrics collection
- **Grafana**: Metrics dashboards
- **Kafka Exporter**: For exposing Kafka metrics to Prometheus
- **(Optional) Elasticsearch & Kibana**: For log/event analytics

## 6. Data Integration
- **MongoDB**: For integration exercises (local via Docker or managed)

## 7. CI/CD
- **GitHub Actions**: For automated testing and deployment
- **Jenkins**: Optional, for advanced CI/CD pipelines

## 8. Managed Services
- **Confluent Cloud**: Managed Kafka (free tier available)
- **AWS MSK / EKS / ECS**: Managed Kafka and Kubernetes (AWS Free Tier for new accounts)

## 9. Security
- **SSL**: For securing Kafka connections (start here)
- **SASL/ACLs**: Optional, for advanced security

## 10. REST APIs & Microservices
- **FastAPI** (Python), **Spring Boot** (Java), **Express** (Node.js): For microservices-first architecture

---

## Setup Checklist
- [ ] Docker & Docker Compose installed
- [ ] Git installed
- [ ] Python, Java, Node.js installed
- [ ] Minikube or Kind + kubectl installed
- [ ] Prometheus, Grafana, Kafka Exporter ready
- [ ] MongoDB available (local or managed)
- [ ] Accounts for Confluent Cloud and AWS
- [ ] FastAPI, Spring Boot, Express sample projects scaffolded

---

## Notes
- Refer to this document as you progress. Update with commands, troubleshooting tips, and additional tools as needed.
- For installation commands and platform-specific notes, see the project README or ask for detailed instructions.
