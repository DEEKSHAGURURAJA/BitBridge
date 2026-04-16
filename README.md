Author
DEEKSHA G
High-Performance Caching & Rate-Limiting To ensure sub-10ms redirection latencies, VortexGate utilizes Redis as a Speed Layer.
Caching: Frequently accessed URLs are cached in-memory to bypass MySQL overhead.

Rate-Limiting: Implements a sliding-window "Bouncer" to protect the infrastructure from automated bot spam.

Multi-Tenant Security & User Auth The system is built on a Private Dashboard model.
Spring Security: Integrated Basic Auth ensures that only authenticated users (e.g., 'hari') can manage their own link inventory.

Session Persistence: Links are tied to a User entity, preventing "data leaking" between different accounts.

Intelligent Conflict Resolution VortexGate handles data integrity through two specific mechanisms:
Duplicate Detection: Before generating a new link, the system performs a hash check on the originalUrl to prevent database bloat.

Custom Aliases: Users can override the Base62 algorithm with personalized "slugs," with the backend automatically validating availability to prevent collisions.

Deep Forensic Analytics Every click triggers a background event that captures:
IP Fingerprinting: Records the network origin of the request.

User-Agent Parsing: Identifies the Browser, OS, and Device Type for every redirection.

🛠️ The Tech Stack Backend: Java 21, Spring Boot 3, Hibernate (JPA).

Speed/Security: Redis, Spring Security.

Relational: MySQL 8.0.

Orchestration: Docker Compose (3-container stack).

📦 Deployment Logic Build: mvn clean package -DskipTests

Launch: docker-compose up -d --build
