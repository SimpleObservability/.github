# Simple: Observability - Health Metadata Schema

## Overview

The Simple: Observability health metadata schema is a standardized JSON format for exposing service health and extra metadata information. Services that implement this schema can be monitored by the Simple: Observability Dashboard.

## Schema Definition

### Required Fields

| Field | Type | Description | Example |
|-------|------|-------------|---------|
| `serviceName` | string | The name of your service | `"Payment API"` |
| `version` | string | Version identifier (semantic version, git branch, commit hash, etc.) | `"1.2.3"`, `"feature/new-feature"`, `"abc123"` |
| `environment` | string | Environment where service is running | `"Production"`, `"UAT"`, `"DEV"` |
| `status` | string | Health status: `"healthy"`, `"degraded"`, or `"unhealthy"`. *Has to be from this fixed list.* | `"healthy"` |
| `timestamp` | string (ISO 8601) | When health check was performed | `"2024-01-15T10:30:00Z"` |

### Optional Fields

| Field | Type | Description | Example |
|-------|------|-------------|---------|
| `description` | string | Additional details about the current status | `"All systems operational"` |
| `hostName` | string | Hostname or machine name | `"web-server-01"` |
| `uptime` | string (ISO 8601 duration) | Time since service started | `"P1DT2H30M"` |
| `additionalMetadata` | object | Key-value pairs of custom metadata | `{"database": "Connected", "cache": "Redis"}` |

## JSON Examples

### Minimal Example

```json
{
  "serviceName": "My API",
  "version": "1.0.0",
  "environment": "Production",
  "status": "healthy",
  "timestamp": "2024-01-15T10:30:00Z",
}
```

### Complete Example

```json
{
  "serviceName": "Payment API",
  "version": "2.3.1",
  "environment": "Production",
  "status": "healthy",
  "timestamp": "2024-01-15T10:30:00Z",
  "description": "All systems operational",
  "hostName": "payment-api-01",
  "uptime": "P7DT5H30M",
  "additionalMetadata": {
    "database": "PostgreSQL 15.2 - Connected",
    "cache": "Redis 7.0 - Connected",
    "queueDepth": "42",
    "region": "us-west-2"
  }
}
```

### Example with Git Branch as Version

```json
{
  "serviceName": "User Service",
  "version": "feature/new-authentication",
  "environment": "DEV",
  "status": "degraded",
  "description": "Testing new authentication flow",
  "additionalMetadata": {
    "commit": "abc123def456",
    "branch": "feature/new-authentication"
  }
}
```

## Health Status Values

| Value | Description |
|-------|-------------|
| `"healthy"` | Service is operating normally |
| `"degraded"` | Service is operational but experiencing issues |
| `"unhealthy"` | Service is not functioning correctly |


## Best Practices

1. **Always include required fields**: Yes, captain obvious.

2. **Use meaningful versions**: Whether semantic versioning or git references, make it identifiable.

3. **Update status appropriately**: Don't always return "healthy" - reflect actual service state.

4. **Include useful metadata**: Add information that helps with troubleshooting (database status, cache connectivity, etc.).

5. **Keep responses fast**: Health checks should return quickly (< 1 second).

6. **Make it accessible**: The `/healthz` endpoint should not require authentication for monitoring purposes.

7. **Use UTC timestamps**: Always use UTC time for consistency across regions.

---
