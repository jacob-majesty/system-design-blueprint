# Project Charter and Technical Template

This document defines the architectural, operational, and development standards for all microservices within this ecosystem.

## 1. Architecture and Design Philosophy

We adhere to a **Polyglot Microservices Architecture**, focusing on **API Contract First** design and continuous, pragmatic documentation.

### A. System Design Documentation (Docs Folder)

All major design decisions and system maps are captured in the `./docs` directory using the following hierarchical structure:

| Level | Diagram/Document | Purpose |
|-------|------------------|---------|
| **L1** | System Context Diagram | Shows the system and its primary external dependencies (users, payment gateways, external APIs) |
| **L2** | Container Diagram | Maps the system's runtime architecture, defining all microservices, API Gateway, databases, and message brokers |
| **L3** | Component Diagram | Detailed view within each microservice/container, showing key modules, function names, and internal data flow |
| **Flow** | Sequence Diagrams | Documents key functional flows (e.g., user registration, critical transaction processing) |
| **API/DB Schemas** | OpenAPI & ERDs | Comprehensive documentation for all API endpoints and database structures |

### B. Architectural Decision Records (ADRs Folder)

The `./adr` folder contains **Architectural Decision Records** for structural, strategic, and practical decisions that are hard to change (e.g., framework choice, database selection, messaging protocol). Smaller technical choices are logged in Decision Logs within the relevant service's documentation.

### C. Clean Code and Naming Conventions

- **Clean Code**: Prioritize readability, simplicity, and maintainability
- **Good Naming**: Use descriptive, intention-revealing names for all variables, functions, and classes
- **Strategic TODOs**: Use specific TODO comments (e.g., `TODO(performance)`, `TODO(security-review)`) for future, strategic improvements

## 2. Technology Stack & Core Components

### A. Core Frameworks (Polyglot Focus)

- **Primary Backend**: Spring Boot (Java 21+), Spring MVC, Spring Data JPA
- **Polyglot**: Create base Service Templates for both Spring Boot and Jakarta EE to facilitate consistent implementation across different languages/frameworks if required

### B. Microservices Infrastructure (Spring Cloud Ecosystem)

| Component | Technology | Purpose |
|-----------|------------|---------|
| Service Discovery | Eureka Service | Dynamic registration and lookup of all microservices |
| Edge Routing | API Gateway (Spring Cloud Gateway) | Single entry point, load balancing, rate limiting, and preliminary security checks |
| Centralized Config | Cloud Config Server | Externalized, version-controlled configuration for all services |
| Event Messaging | Spring Cloud Bus / RabbitMQ | Asynchronous communication and configuration change propagation |
| Resilience | Resilience4j | Implementing circuit breakers, bulkheads, retries, and rate limiting for fault tolerance |
| Load Balancer | Client-side (e.g., Ribbon/Integrated in Gateway) | Distributing traffic efficiently across multiple service instances |
| API Documentation | SpringDoc OpenAPI 3 | Automatically generates the OpenAPI spec and provides a Swagger UI from the code annotations |

### C. Data Persistence

We utilize a multi-database approach, selecting the best tool for the specific job (**Data Consistency is paramount for critical operations**).

| Database | Primary Use Case | Technology |
|----------|------------------|------------|
| **Primary/Relational** | Data Consistency for critical operations (e.g., financial transactions, user accounts) | PostgreSQL |
| **Flexible/Analytics** | Flexibility for evolving content (e.g., catalogs, user profiles) and analytics data | MongoDB |
| **Cache/Real-Time** | Caching, high Performance for user experience and real-time features (e.g., session state) | Redis |

**Database Migration**: Flyway is mandatory for managing and versioning all PostgreSQL schema changes.

## 3. Development Workflow and Git Standards

### A. Git Flow Strategy

We use a modified Git Flow model based on environments:

- **main**: Production-ready code. Protected branch. Only mergers from staging are allowed via PR
- **staging**: Pre-production environment. Protected branch. Only mergers from dev are allowed via PR. Used for final, safe, production-like testing
- **dev**: Rapid iteration and integration environment. Merges from feature/bugfix branches are allowed
- **Feature Branches**: `feature/*`, `bugfix/*`, `hotfix/*`, `release/*`. These merge into `dev`

### B. Code Review & Merging Policy

- **Merge Requirement**: One (1) senior engineer approval (or my approval, as specified) is required before merging into `dev`, `staging`, or `main`
- **Git Hooks**: Mandatory local Git hooks are configured to enforce pre-commit quality checks (e.g., linting, static analysis) to maintain code quality
- **Semantic Versioning**: All releases and tags MUST follow Semantic Versioning (MAJOR.MINOR.PATCH)
- **Git Tagging**: The `release/*` branches must be tagged upon successful merge to `main`

## 4. Project Structure (Monorepo/Multi-module)

The repository follows a centralized, multi-module structure designed for scalability, clear separation of concerns, and infrastructure consistency.

```
project-root/
├── .github/                       # GitHub Actions Workflows & PR Templates
│   ├── workflows/
│   │   ├── ci-cd-pipeline.yml     # Main build/test/deploy process
│   │   ├── quality-checks.yml     # Static analysis, linting
│   │   └── security-scan.yml      # Dependency and SAST scans
├── adrs/                          # Architecture Decision Records
├── docs/                          # System Design, Schemas, & Operational Docs
│   ├── architecture/              # L1, L2, L3 Diagrams & Sequence Flows
│   └── database/                  # Schema documentation (PostgreSQL, MongoDB)
├── microservices/                 # Core business services and infrastructure components
│   ├── service-template-springboot/ # Base project for Spring services
│   │   ├── src/
│   │   │   ├── main/
│   │   │   │   └── resources/
│   │   │   │       └── db/migration/ (Flyway scripts)
│   │   └── Dockerfile
│   ├── service-template-jakartaee/  # Base project for non-Spring services
│   ├── api-gateway/
│   ├── service-discovery/
│   └── auth-service/
├── shared/                        # Reusable code and contracts
│   ├── common-lib/                # Common util libraries (tracing, security, errors)
│   └── api-contracts/             # Generated client stubs / interface definitions
├── infrastructure/                # Deployment and environment configuration
│   ├── docker/                    # Docker Compose files for local/dev environments
│   ├── kubernetes/                # Base K8s/Kustomize manifests / Helm Charts
│   └── monitoring/                # Prometheus/Grafana configs
├── scripts/                       # Local automation (git hooks, deployment, testing)
│   ├── git-hooks/                 # Pre-commit, pre-push enforcement
│   └── deployment/                # Rollback and health check scripts
├── frontend/                      # Frontend 
├── tests/                         # Dedicated folder for E2E and UAT (Selenium)
├── config/                        # Centralized application property files
├── pom.xml (Parent Maven)         # Defines dependencies and global plugin versions
└── README.md (Comprehensive)      # Project entry point and setup guide
```

## 5. Quality and Testing Strategy

### A. Testing Pyramid

- **Unit Tests**: Mandatory for all business logic. Tools: JUnit 5. Coverage enforced by JaCoCo
- **Integration Tests**: Focus on service boundaries, database access, and external API interactions. Tools: JUnit 5, Testcontainers (for ephemeral, realistic DB testing)
- **Data Integrity Tests**: Specific tests ensuring data consistency and migration correctness
- **Monitoring and Observability**: Essential to validate system behavior in staging and production
- **User Acceptance Testing (UAT)**: Conducted using automation tools like Selenium for critical end-to-end user journeys

### B. Testing Tools and Techniques

- **Testcontainers**: Used for spinning up disposable PostgreSQL, MongoDB, Redis, and RabbitMQ instances for reliable, isolated integration testing
- **Jacoco**: Code coverage reports are generated and checked during the CI process

## 6. CI/CD and Deployment (GitHub Actions)

The CI/CD pipeline is managed via GitHub Actions and includes mandatory sequential stages:

1. **Quality Checks**: Runs linting, format checks, and enforces static analysis (SonarQube/SpotBugs checks)
2. **Security Scans**: Executes dependency vulnerability and basic static application security testing (SAST) scans
3. **Test**: Runs all Unit Tests and Integration Tests (with Testcontainers). Enforces JaCoCo coverage thresholds
4. **Build**: Compiles the service, creates the Docker image, and pushes it to the registry

### Operational and Deployment Standards

- **Rollback Strategy**: All deployments must have a tested, one-click rollback mechanism (e.g., reverting to the previous successful Docker image/K8s deployment)
- **Deployment Target**: All services are deployed as Docker containers. Future planning includes migration to Kubernetes (k8s) for orchestration

## 7. Observability and Operations

### A. Monitoring

- **Metrics**: Exposed via Spring Boot Actuator endpoints
- **Collection**: Scraped by Prometheus
- **Visualization**: Presented in dynamic dashboards via Grafana
- **Performance**: Dedicated monitoring for API response times and resource utilization in staging and production

### B. Logging and Troubleshooting

- **Logs**: Standardized format (JSON preferred) and centralized logging stack required
- **Distributed Tracing**: MANDATORY implementation for cross-service debugging and performance monitoring. All services must forward tracing headers (e.g., using OpenTelemetry)

### C. Security

- **Authentication/Authorization**: Managed via Spring Security utilizing OAuth2 and OpenID Connect
- **API Security**: Rate limiting enforced at the API Gateway level
- **Network Isolation**: Microservices are run on a private, isolated network segment where communication is strictly controlled
- **Health Checks**: Standardized Actuator health checks are exposed for load balancer and orchestration (k8s) readiness/liveness probes

### D. Real-World Implementation Tips

- **Error Handling**: Implement consistent error handling (standardized HTTP status codes and response bodies) across all services
- **Communication Patterns**: Clearly document communication patterns (synchronous vs. asynchronous) in the L3 component diagrams and sequence diagrams
- **Comprehensive Readme**: Every service repository must contain a detailed README.md covering setup, dependencies, build/test commands, and deployment details
