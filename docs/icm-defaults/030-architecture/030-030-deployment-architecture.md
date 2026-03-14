# Deployment Architecture

> Status: Draft  
> Owner: TBD  
> Last updated: 2026-01-10

## Technology Stack

| Layer | Technology |
|-------|-----------|
| **Runtime** | .NET 10 / C# |
| **Containerization** | Docker |
| **Orchestration (Local)** | .NET Aspire AppHost |
| **Orchestration (Prod)** | TBD (Kubernetes/AKS, ACA, or equivalent) |

---

## Local Development Environment

### .NET Aspire AppHost

The Aspire AppHost (`{{ PRODUCT_NAME }}.AppHost`) provides:
- **Service discovery** and configuration wiring
- **Local container orchestration** (via Docker Compose integration)
- **OTEL defaults** (telemetry plumbing)
- **Developer dashboard** for observability during development

### Container Topology (Local)

```
┌─────────────────────────────────────────┐
│  APIM/Gateway (API Gateway)             │
└─────────────────────────────────────────┘
              ↓
┌─────────────────────────────────────────┐
│  Domain Microservices (containers)      │
│  - Basket API                           │
│  - Catalog API                          │
│  - Ordering API                         │
│  - Identity API                         │
│  - Webhooks API                         │
└─────────────────────────────────────────┘
              ↓
┌─────────────────────────────────────────┐
│  Infrastructure Services (containers)   │
│  - PostgreSQL                           │
│  - Redis                                │
│  - RabbitMQ (Event Bus placeholder)    │
└─────────────────────────────────────────┘
              ↓
┌─────────────────────────────────────────┐
│  Workers (background processors)        │
│  - Event consumers                      │
│  - Read model updaters                  │
│  - Projection workers                   │
└─────────────────────────────────────────┘
```

---

## Production Environments

### Environment Strategy

| Environment | Purpose |
|-------------|---------|
| **Dev** | Integration testing, early validation |
| **Test/Staging** | Pre-production validation, performance testing |
| **Prod** | Live system |

**Infrastructure provisioning:** TBD (IaC via Terraform/Bicep)

### Container Topology (Production)

Every microservice and worker runs as a **container**:

**API Layer:**
- API Gateway/APIM container
- Domain API containers (1+ instances per service)

**Worker Layer:**
- Event consumer workers
- Read model projection workers
- ETL/integration workers

**Data Layer:**
- Managed services (Azure SQL, Cosmos DB, etc.) OR
- Containerized databases with persistent volumes (non-prod)

**Messaging Layer:**
- Event Hub (managed service)
- Service Bus (managed service)

**Observability:**
- OTEL Collector (container)
- Monitoring backend (managed service or self-hosted)

---

## Deployment Patterns

### Blue-Green Deployment
- Maintain two identical production environments
- Route traffic via gateway/load balancer
- Zero-downtime deployments

### Rolling Updates
- Gradually replace container instances
- Health checks ensure stability before proceeding

### Event Versioning Strategy
- Event schemas are versioned
- Consumers handle multiple event versions during transition periods
