# Architecture

## Technology Stack

- **.NET 9** (current stable)
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
├── {MicroserviceName}.csproj
├── Program.cs
├── appsettings.json
├── Controllers/          → API endpoints
├── Services/            → Business logic
├── Models/              → Request/Response DTOs
├── Data/                → Database context, repositories
└── Infrastructure/      → Exceptions, middleware, utilities
```

## Solution File (.sln)

For multi-service repos, use a solution file at the repo root:

```
MyProject.sln
├── src/ServiceA/ServiceA.csproj
├── src/ServiceB/ServiceB.csproj
├── tests/ServiceA.Tests/ServiceA.Tests.csproj
└── tests/ServiceB.Tests/ServiceB.Tests.csproj
```

The `/dev-scaffold` skill creates or updates the `.sln` file automatically when scaffolding a new service. To manage manually:

```bash
dotnet new sln -n MyProject                           # create solution
dotnet sln add src/ServiceA/ServiceA.csproj            # add project
dotnet sln add tests/ServiceA.Tests/ServiceA.Tests.csproj  # add test project
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

## Skills Workflow

```
/dev-scaffold (creates structure + boilerplate)
    ↓
/dev-implement (writes production code + wires DI)
    ↓
/test (writes unit + integration tests + coverage analysis)
    ↓
/review (checks quality, security, compliance)
    ↓
/docs (updates technical design, API docs)
    ↓
Git commit
```
