# Microservices Patterns

Fill this file with your team's service communication patterns. Example structure:

## Synchronous Communication (HTTP/REST)
- Use `IHttpClientFactory` (never `new HttpClient()`)
- Configure named/typed HTTP clients in DI
- Implement retry policies with Polly
- Circuit breaker for failing dependencies

## Asynchronous Communication (Events)
- Azure Service Bus for reliable messaging
- Event-driven architecture for cross-service updates
- Dead-letter queue monitoring and handling
- Idempotent message processing

## API Gateway
- Single entry point for external consumers
- Route to internal microservices
- Centralized authentication/rate limiting

## Service Discovery
- Azure-managed service endpoints
- Configuration-based service URLs (not hardcoded)

## Data Patterns
- Each service owns its database (no shared databases)
- Eventual consistency for cross-service data
- Saga pattern for distributed transactions
- Outbox pattern for reliable event publishing

## Health Checks
- `/health` endpoint on every service
- Check database connectivity
- Check downstream service availability
- Use `Microsoft.Extensions.Diagnostics.HealthChecks`
