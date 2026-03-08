# Azure Best Practices

Fill this file with your team's Azure service patterns. Example structure:

## Azure Key Vault
- Store all secrets, connection strings, and certificates
- Access via managed identity (no client secrets in code)
- Configuration: `builder.Configuration.AddAzureKeyVault(...)`

## Azure SQL Database
- Use Entity Framework Core with migrations
- Connection string from Key Vault
- Enable retry logic for transient failures

## Azure Cosmos DB
- Use for document/NoSQL workloads
- Partition key strategy documentation
- Request unit budgeting

## Application Insights
- Enable for all services
- Custom telemetry for business events
- Structured logging with ILogger

## Azure Service Bus
- Event-driven communication between services
- Dead-letter queue handling
- Message retry policies

## Managed Identity
- Use for all Azure service-to-service auth
- No client secrets or certificates in code
- DefaultAzureCredential for local development
