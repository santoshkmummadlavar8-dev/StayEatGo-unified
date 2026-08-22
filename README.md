# StayEatGo-unified
StayEatGo-Unified  is Operating System for Global Travel Services

### 1. The "Go" Logistics & Dispatch Engine
* **Dynamic Ride-Matching:** Utilises Redis geospatial indexes (`GEOADD` and `GEOSEARCH`) alongside H3 hexagonal spatial grid hashing to calculate optimal driver-traveler dispatch loops in sub-millisecond times.
* **Concurrency & Safety:** Leverages Redisson distributed locking to eliminate race conditions, ensuring a driver is never double-allocated and a trip lifecycle transition remains thread-safe.
* **Auto-Escalation State Machine:** Features an asynchronous retry mechanism that automatically flags non-responsive drivers within 15 seconds, rolls back the offer, and escalates to the next nearest driver.

### 2. Autonomous IoT & Hospitality Automation
* **Proximity-Triggered Pipelines:** Processes geofenced proximity data to automate check-ins when guests arrive at a lodge.
* **Just-In-Time Cab Dispatch:** Automatically schedules and dispatches outbound transportation ("Go" engine integration) dynamically upon guest check-out.

### 3. Reactive Real-Time Telemetry Pipeline
* **High-Frequency Ingestion:** Establishes persistent WebSockets streams to digest driver location telemetry packets every 3 seconds.
* **Reactive UI Syncing:** Pushes live coordinate streams immediately to travelers’ React-based Leaflet maps and updates merchant kitchen display terminals as delivery drivers approach.

### 4. Production-Grade Observability
* **Virtual Thread Tracking:** Built on Java 21's Virtual Threads (Project Loom) to process high-concurrency sockets smoothly under massive parallel loads.
* **Scraping & Monitoring:** Configured with Prometheus and Grafana to collect and visualise JVM metrics, WebSocket connection states, and active transaction volumes on a tight 5-second interval.

---

## 🛠️ The Tech Stack

* **Backend:** Java 21 (Virtual Threads), Spring Boot 3.4, Spring Security, Spring WebSockets, JPA / Hibernate, Flyway Migrations
* **Frontend:** React 18, TypeScript, Vite, Tailwind CSS, Leaflet / OpenStreetMap (Dynamic Spatial Overlay), TanStack Query
* **Data & Distributed Caching:** PostgreSQL 17 (Primary relational engine with strict schema constraints) + Redis (Distributed lock registry, session caching, and geospatial indexer)
* **Observability:** Prometheus, Grafana, Alertmanager
* **Deployment:** Docker, Kubernetes (K8s) engine manifests
