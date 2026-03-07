# Architecture

## Technology Stack

- **.NET 10** (latest)
- **C#** (production language)
- **xUnit** (testing framework)
- **Azure SQL / Cosmos DB** (data storage)
- **Azure Key Vault** (secrets management)
- **Moq** (mocking library)
- **Dependency Injection** (built-in)

## Design Principles

1. **Async/Await** - All I/O operations are asynchronous
2. **Dependency Injection** - Loose coupling, testability
3. **Repository Pattern** - Data access abstraction
4. **Single Responsibility** - Clear, focused methods
5. **Security First** - No hardcoded secrets, input validation
6. **Test-Driven** - Minimum 80% code coverage

## Microservice Structure

Each microservice follows standard .NET structure:

```
{MicroserviceName}/
├── Controllers/          → API endpoints
├── Services/            → Business logic
├── Models/              → Request/Response DTOs
├── Data/                → Database context, repositories
└── Infrastructure/      → Exceptions, middleware, utilities
```

## Communication Patterns

- **HTTP/REST** - Synchronous service-to-service calls
- **Events** - Asynchronous via message queue (documented in context)
- **Dependency** - Services can depend on others via HTTP clients

## Security

- Secrets stored in Azure Key Vault (never in code)
- JWT token authentication
- Role-based authorization
- Input validation on all endpoints
- Secure logging (no PII)

## Testing Strategy

- **Unit Tests** - Test individual methods with mocked dependencies
- **Integration Tests** - Test API endpoints with in-memory database
- **Coverage Target** - Minimum 80% of code

## Documentation

- Technical design per microservice
- API documentation per endpoint
- Implementation details documented
- Security considerations recorded

## Agent Workflow

```
Developer Agent (writes code)
    ↓
Test Agent (writes tests, checks coverage)
    ↓
Review Agent (checks quality, security, compliance)
    ↓
Documentation Agent (updates technical design, API docs)
    ↓
Git commit
```
