<h1 align="center">Simple: Observability</h1>

<div align="center">
  <i>A simple, lightweight observability tool for monitoring services.</i>
</div>

## Summary

  Simple: Observability is a lightweight web dashboard for monitoring the health of your services across multiple environments (DEV, UAT, PROD, etc). It uses a straightforward health check schema that can be implemented in any technology stack, making it easy to integrate with your existing services.

  <img width="1496" height="722" alt="image" src="https://github.com/user-attachments/assets/5ab46b14-e8c2-4aee-8dea-0ef3d4160d65" />


## Health Check Schema

Have any endpoint in your Api/Website (e.g. `GET /healthz`) expose an  endpoint that returns JSON following the Simple: Observability schema:

```json
{
  "serviceName": "My Service",
  "version": "1.0.0",
  "environment": "Production",
  "status": "healthy",
  "timestamp": "2024-01-15T10:30:00Z"
}
```

See [SCHEMA.md](SCHEMA.md) for complete schema documentation.

## Running the Dashboard

Then run the Simple: Observability dashboard to monitor the health of your services in real-time.

```
docker run -d -p 8080:80 simple-observability:latest
```

## Client Packages

We provide easy-to-use packages for popular languages and frameworks to help you quickly implement health checks that follow the Simple: Observability schema.

| Language/Framework | Package Name | Package Manager | Status |
|-------------------|--------------|----------------|---------|
| **C#/.NET** | `SimpleObservability.AspNetCore` | NuGet | 🚧 Planned |
| **Go** | `github.com/simple-observability/go` | go mod | 🚧 Planned |
| **Rust** | `simple-observability` | Cargo | 🚧 Planned |
| **JavaScript/Node.js** | `simple-observability-js` | npm | 🚧 Planned |
| **Java/Spring Boot** | `simple-observability-spring` | Maven/Gradle | 🚧 Planned |
| **Python** | `simple-observability-python` | pip | 🚧 Planned |
| **PHP/Laravel** | `simple-observability-laravel` | Composer | 🚧 Planned |


Each package will provide:
- ✅ Pre-configured health check endpoints
- ✅ Automatic schema validation  
- ✅ Environment detection
- ✅ Service metadata collection
- ✅ Customizable health checks

## ⚖️ Dual License

**Simple: Observability uses a dual-license model:**

✅ **FREE** for open source projects, students, non-profits, charities, and small businesses (<250 employees or <$1M revenue)  
💼 **Commercial License** required for larger organisations

📄 **[View License Details](LICENSE.md)** | 💰 **[View Pricing](docs/PRICING.md)**

## Features

- 🎯 **Simple Setup**: Just configure your service endpoints and go
- 🐳 **Docker Ready**: Designed to run as a container with volume-mounted configuration
- 🌍 **Multi-Environment**: Display services across DEV, UAT, PROD, or custom environments
- 📊 **Real-time Monitoring**: Auto-refreshing dashboard shows service health at a glance
- 🔧 **Flexible Schema**: Standard health check format that works with any technology stack
- 📦 **Language Libraries**: Easy-to-use libraries for helping you easily return the valid JSON schema responses.
- ⚙️ **Settings UI**: Manage configuration directly from the web interface

---