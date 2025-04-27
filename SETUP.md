# Kafka Learning Environment Setup

This document outlines all the tools, frameworks, and services required for your Kafka mastery journey, along with installation and setup notes for each. Use this as a checklist and reference as you build out your learning environment.

---

## 1. Core Tools
- **Docker & Docker Compose**: For running Kafka, Zookeeper, MongoDB, and supporting services locally.
- **Git**: For version control and collaboration.

## 2. Programming Languages & Frameworks
- **Python**: For producers/consumers and microservices (FastAPI)
- **Java**: For producers/consumers, Kafka Streams, and microservices (Spring Boot)
  - **Maven** and **Gradle**: Java build tools (installed)
- **Node.js**: For producers/consumers and microservices (Express)

## 3. Kafka Ecosystem
- **Apache Kafka**: Core messaging platform (local via Docker, managed via Confluent Cloud/AWS MSK, or **GKE Autopilot via Helm/Bitnami**)
- **Kafka Connect**: For integrating with MongoDB and other data sources/sinks
- **Kafka Streams**: For stream processing (Java)
- **ksqlDB**: Optional, for SQL-like stream processing

## 4. Orchestration
- **Kubernetes**: For orchestrating multi-service deployments
  - ~~**Minikube** or **Kind**: Lightweight local Kubernetes clusters~~ (removed; using **GKE Autopilot via Google Cloud**)
  - **kubectl**: Kubernetes command-line tool
  - **Google Cloud SDK**: For managing GKE clusters
  - **GKE (Google Kubernetes Engine)**: Cloud Kubernetes service (**Autopilot** mode tested)

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
- **SASL/ACLs**: Enabled by default in Bitnami Helm chart (tested)

## 10. REST APIs & Microservices
- **FastAPI** (Python), **Spring Boot** (Java), **Express** (Node.js): For microservices-first architecture

---

## Setup Checklist
- [x] Docker & Docker Compose installed
- [x] Git installed
- [x] Python, Java, Node.js, Maven, Gradle installed
- [x] Docker Desktop installed and running
- [x] GKE Autopilot cluster created and healthy
- [x] Kafka and Zookeeper deployed on GKE via Helm/Bitnami
- [x] Kafka CLI client pod deployed and tested (produce/consume messages)
- [ ] Docker Compose file for local Kafka/Zookeeper
- [ ] Kafka and Zookeeper containers running locally
- [ ] Producers/consumers tested locally
- [ ] Prometheus, Grafana, Kafka Exporter ready
- [ ] MongoDB available (local or managed)
- [ ] Accounts for Confluent Cloud and AWS
- [ ] FastAPI, Spring Boot, Express sample projects scaffolded

### How to Run Kafka and Zookeeper on GKE Autopilot

1. **Create GKE Autopilot cluster** in your preferred region (e.g., `us-central1`).
2. **Install Helm** and add the Bitnami repo:
   ```sh
   helm repo add bitnami https://charts.bitnami.com/bitnami
   helm repo update
   ```
3. **Create a namespace for Kafka:**
   ```sh
   kubectl create namespace kafka
   ```
4. **Deploy Zookeeper:**
   ```sh
   helm install zookeeper bitnami/zookeeper --namespace kafka
   ```
5. **Deploy Kafka:**
   ```sh
   helm install kafka bitnami/kafka --namespace kafka
   ```
6. **Troubleshooting:**
   - If Zookeeper or Kafka pods are stuck in `Pending`, check for resource quota or PVC affinity issues.
   - Delete and recreate PVCs if necessary to resolve zone conflicts.
   - Monitor with:
     ```sh
     kubectl get pods -n kafka -o wide
     kubectl describe pod <pod-name> -n kafka
     ```

7. **Test with Kafka client pod:**
   - Deploy a CLI pod:
     ```sh
     kubectl run kafka-client --restart='Never' --image docker.io/bitnami/kafka:4.0.0-debian-12-r3 --namespace kafka --command -- sleep infinity
     ```
   - Copy your `client.properties` file (with SASL credentials) into the pod and test producing/consuming messages.

---

## Troubleshooting Notes
- **PVC Affinity/Quota:** GKE Autopilot may bind PVCs to zones with no available nodes. If pods are unschedulable, delete and recreate the StatefulSet and PVC to allow rebinding in a zone with available resources.
- **Authentication:** Bitnami Kafka uses SASL/SCRAM by default. Extract the password from the `kafka-user-passwords` secret and use it in your client configuration.
- **Scaling:** Autopilot manages node scaling, but you may need to request quota increases for large clusters.

---

## Next Steps: Java/Python/Node.js Producers & Consumers
- Scaffold sample producer/consumer projects in Java, Python, and Node.js.
- Build Docker images for each and deploy as Kubernetes pods in the `kafka` namespace.
- Use internal DNS (`kafka.kafka.svc.cluster.local:9092`) and the same SASL credentials for connectivity.
- Test message flow between microservices and Kafka topics.

---

_You now have a cloud-native, production-like Kafka environment ready for microservices development and experimentation!_

---

## Notes
- Refer to this document as you progress. Update with commands, troubleshooting tips, and additional tools as needed.
- For installation commands and platform-specific notes, see the project README or ask for detailed instructions.
