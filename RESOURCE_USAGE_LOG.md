# Resource Usage Log & Checkpoints

This file documents system resource usage checkpoints to help monitor how RAM, CPU, and swap usage change as more services, containers, and clusters are started during the Kafka learning journey. Use this log to track trends, identify bottlenecks, and optimize resource allocation.

---

## Checkpoint 1: Pre-Minikube, Docker Running, Windsurf Active

**Date/Time:** 2025-04-25 17:31 PDT

**System:**
- Physical Memory: 16.00 GB
- Memory Used: 8.09 GB
- Cached Files: 4.88 GB
- Swap Used: 446.8 MB
- App Memory: 4.10 GB
- Wired Memory: 2.98 GB
- Compressed: 1,022.0 MB
- Memory Pressure: Low (green)

**Major Processes:**
- Windsurf IDE (multiple processes, 3–4 GB total)
- Docker Desktop & VM (several processes, ~0.5 GB)
- System processes (WindowServer, mds_stores, etc.)

**Notes:**
- System is healthy, with ~8 GB RAM used and ~8 GB available (much of it cached).
- Swap and compression are in use but not excessive.
- Plenty of headroom for starting Minikube and additional containers.
- Will monitor how these values change as more services are started.

---

## Checkpoint 2: After Starting Minikube (2GB RAM, 2 CPUs)

**Date/Time:** 2025-04-25 17:43 PDT

**System:**
- Physical Memory: 16.00 GB
- Free RAM: ~307 MB (76,588 pages × 4 KB)
- Docker Images: 10 (10.17 GB total, 9.58 GB reclaimable)
- Docker Containers: 2 (1 active, 3.9 MB)
- Docker Volumes: 3 (1.74 GB)
- Build Cache: 30.58 MB

**Major Processes:**
- Minikube cluster running (2GB RAM, 2 CPUs allocated)
- Docker Desktop & VM
- Windsurf IDE
- System/background processes

**Notes:**
- Significant reduction in free RAM after starting Minikube (expected).
- Docker disk usage reduced after pruning, but still using ~10 GB for images.
- System is still responsive, but available RAM is now limited—monitor closely as more services are started.

---

## Checkpoint 3: Activity Monitor After Minikube Start

**Date/Time:** 2025-04-25 17:46 PDT

**System:**
- Physical Memory: 16.00 GB
- Memory Used: 11.83 GB
- Cached Files: 4.08 GB
- Swap Used: 575.5 MB
- App Memory: 7.64 GB
- Wired Memory: 3.10 GB
- Compressed: 1.08 GB
- Memory Pressure: Low (green)

**Notes:**
- RAM usage increased significantly after starting Minikube.
- Swap and compression are in use, but system remains responsive.
- Still within healthy limits, but close to high usage—monitor as more services are deployed.

---

## Checkpoint 4: After Docker Cleanup & Minikube Restart

**Date/Time:** 2025-04-25 17:57 PDT

**System:**
- Physical Memory: 16.00 GB
- Free RAM: ~58 MB (14,763 pages × 4 KB)
- Docker Images: 5 (7.55 GB total, 6.87 GB reclaimable)
- Docker Containers: 2 (1 active, 454.7 kB)
- Local Volumes: 3 (1.67 GB)
- Build Cache: 4.42 GB

**Major Processes:**
- Minikube cluster running (2GB RAM, 2 CPUs allocated)
- Docker Desktop & VM
- Windsurf IDE
- System/background processes

**Notes:**
- Substantial Docker disk usage reduction after removing unused images/containers.
- Free RAM is now very low; system is still operational but monitor closely as more services are started.
- Build cache could be further pruned if more space is needed.

---

## Checkpoint 5: After Minikube Cluster Verification

**Date/Time:** 2025-04-25 18:10 PDT

**System:**
- Physical Memory: 16.00 GB
- Free RAM: ~22 MB (5,733 pages × 4 KB)
- Docker Images: 7 (8.88 GB total, 8.08 GB reclaimable)
- Docker Containers: 2 (1 active, 2.93 MB)
- Local Volumes: 3 (1.54 GB)
- Build Cache: 4.42 GB

**Major Processes:**
- Minikube cluster running (2GB RAM, 2 CPUs allocated)
- Docker Desktop & VM
- Windsurf IDE
- System/background processes

**Notes:**
- Free RAM is extremely low, but system remains operational.
- Docker disk usage increased slightly due to Minikube recreation (new images pulled).
- Monitor closely as you deploy additional services.

---

## Checkpoint 6: After Removing Minikube/Kubectl, Preparing for Docker Compose

**Date/Time:** 2025-04-25 18:22 PDT

**System:**
- Physical Memory: 16.00 GB
- Free RAM: ~195 MB (50,024 pages × 4 KB)
- Docker Images: 7 (8.88 GB total, 8.60 GB reclaimable)
- Docker Containers: 1 (0 active, 49.15 kB)
- Local Volumes: 2 (595 MB)
- Build Cache: 4.42 GB

**Major Processes:**
- Docker Desktop & VM (Minikube and Kubernetes tools uninstalled)
- Windsurf IDE
- System/background processes

**Notes:**
- Minikube and kubectl uninstalled, freeing up disk and RAM.
- Free RAM increased significantly.
- Next: Set up Kafka/Zookeeper using Docker Compose for a lighter, resource-friendly workflow.

---

## Checkpoint 8: After Reducing Docker Desktop Memory to 4GB

**Date/Time:** 2025-04-25 18:41 PDT

**System:**
- Physical Memory: 16.00 GB
- Free RAM: ~5.6 GB (1,472,358 pages × 4 KB)
- Docker Images: 9 (9.90 GB total, 8.49 GB reclaimable)
- Docker Containers: 3 (0 active, 188 kB)
- Local Volumes: 7 (662.5 MB)
- Build Cache: 4.42 GB

**Major Processes:**
- Docker Desktop & VM (now limited to 4GB RAM)
- Windsurf IDE
- System/background processes

**Notes:**
- Reducing Docker Desktop memory to 4GB freed up significant RAM for other applications.
- System is much more responsive, and resource pressure is lower.
- Kafka/Zookeeper development remains feasible with this limit for typical workloads.

---

## Checkpoint 9: After Volume Cleanup and Kafka CLI Test

**Date/Time:** 2025-04-25 19:03 PDT

**System:**
- Docker Desktop (4GB RAM limit)
- Kafka and Zookeeper containers running
- All Docker volumes cleaned up (no persistent data from previous runs)

**Actions:**
- Removed all Docker volumes to resolve Zookeeper/Kafka startup errors.
- Restarted containers with `docker-compose up -d`.
- Verified Kafka CLI tools work: successfully produced and consumed messages on a test topic.

**Notes:**
- Kafka/Zookeeper now start cleanly with no stale state.
- CLI tools are fully functional for local development and learning.

---

_Add additional checkpoints below as you spin up Kafka, Zookeeper, MongoDB, Minikube clusters, etc._
