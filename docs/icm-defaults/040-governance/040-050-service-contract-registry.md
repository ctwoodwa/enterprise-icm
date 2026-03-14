# Service Contract Registry

> Status: Draft  
> Owner: Architecture Team  
> Last updated: 2026-01-22

## Central Registry Structure

Central registry for all service interfaces:

```
contract-registry/
├── services/
│   ├── asset-service/
│   │   ├── openapi-v1.yaml
│   │   ├── openapi-v2.yaml
│   │   ├── events/
│   │   │   ├── AssetConditionChanged-v1.json
│   │   │   └── AssetConditionChanged-v2.json
│   │   └── consumers/
│   │       ├── Asset.Web-pact.json
│   │       └── WorkOrder.Service-pact.json
│   ├── work-order-service/
│   │   ├── openapi-v1.yaml
│   │   └── events/
│   │       └── WorkOrderCreated-v1.json
├── platform/
│   ├── messaging-abstractions.yaml
│   └── identity-abstractions.yaml
└── README.md
```

---

## Registry Contents

**For each service:**
- OpenAPI specification (REST APIs)
- Event schema definitions (AsyncAPI)
- gRPC proto files (if using gRPC)
- Consumer contracts (Pact files)

---

## Publishing Workflow

```csharp
// Automatic OpenAPI publishing in service startup
public static class OpenApiRegistration
{
    public static IApplicationBuilder UseContractRegistry(this IApplicationBuilder app)
    {
        var apiSpec = app.GenerateOpenApiSpecification();
        
        // Publish to contract registry
        var registry = app.Services.GetRequiredService<IContractRegistry>();
        registry.PublishAsync(new ServiceContract
        {
            ServiceName = "Asset.Service",
            Version = "v1",
            Specification = apiSpec,
            Type = ContractType.OpenAPI
        });
        
        return app;
    }
}
```

---

## Discovery

Services and clients discover contracts from registry:

```csharp
public class ServiceDiscovery
{
    public async Task<OpenApiDocument> GetServiceSpecAsync(string serviceName, string version)
    {
        return await _registry.GetSpecAsync(serviceName, version);
    }
    
    public async Task<IEnumerable<ServiceContract>> GetAllServicesAsync()
    {
        return await _registry.ListServicesAsync();
    }
}
```

---

## Related Documentation

- [API Versioning](040-020-api-versioning.md)
- [Contract Testing](040-040-contract-testing.md)
- [Breaking Change Detection](040-060-breaking-change-detection.md)
