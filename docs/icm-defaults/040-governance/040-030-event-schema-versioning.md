# Event Schema Versioning

> Status: Draft  
> Owner: Architecture Team  
> Last updated: 2026-01-22

## Event Metadata

All events include schema version in metadata:

```csharp
public abstract record DomainEvent
{
    public string EventType { get; init; }
    public int SchemaVersion { get; init; }  // Explicit version
    public DateTimeOffset Timestamp { get; init; }
    // ...
}

public record AssetConditionChanged : DomainEvent
{
    public AssetConditionChanged()
    {
        EventType = "AssetConditionChanged";
        SchemaVersion = 2;  // Incremented for breaking changes
    }
    
    public string AssetId { get; init; }
    public ConditionScore NewScore { get; init; }
}
```

---

## Event Evolution Rules

**Backward-compatible changes (same schema version):**
- Add optional fields
- Add new event types

**Breaking changes (increment schema version):**
- Remove fields
- Rename fields
- Change field types

---

## Multi-Version Event Handling

Consumers must handle multiple schema versions:

```csharp
public class AssetReadModelUpdater : IEventConsumer
{
    public async Task HandleAsync(DomainEvent @event, EventContext ctx)
    {
        if (@event is AssetConditionChanged acc)
        {
            switch (acc.SchemaVersion)
            {
                case 1:
                    await HandleV1Async((AssetConditionChangedV1)acc);
                    break;
                case 2:
                    await HandleV2Async(acc);
                    break;
                default:
                    _logger.LogWarning("Unknown schema version {Version}", acc.SchemaVersion);
                    break;
            }
        }
    }
}
```

---

## Event Versioning Strategy

**Append-only events:**
- Events in Event Hub are immutable history
- Old schema versions remain in stream forever
- Consumers must handle ALL schema versions they've ever seen

**Schema registry:**
- All event schemas published to central registry
- Consumers download schemas at startup
- Breaking changes detected by comparing schemas

---

## Related Documentation

- [API Versioning](040-020-api-versioning.md)
- [Contract Testing](040-040-contract-testing.md)
- [Service Contract Registry](040-050-service-contract-registry.md)
