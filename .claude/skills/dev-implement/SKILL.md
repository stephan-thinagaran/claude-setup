# Implement Feature

---
context: fork
agent: general-purpose
model: claude-sonnet-4-6
allowed-tools: Write, Edit, Read, Glob, Grep, Bash
---

## Purpose

Write production C# code for a feature: controllers, services, repositories, and models.

## References

Read these before starting:
- `.claude/guard-rails.md`
- `.claude/context/ms-dotnet-patterns.md`
- `.claude/context/azure-best-practices.md`
- `.claude/context/security-standards.md`
- `.claude/context/common-libraries.md`
- `.claude/context/naming-conventions.md`
- `docs/{service}/technical-design.md` (if exists)

## Standards

### Code Patterns
- .NET 9, C#, async/await for all I/O
- Constructor-based dependency injection
- Repository pattern for data access
- Single responsibility per class/method
- PascalCase for classes/methods, camelCase for variables/parameters

### Security
- NO hardcoded secrets — use Azure Key Vault via configuration
- Input validation on all endpoints (use data annotations + FluentValidation)
- Proper authentication/authorization attributes
- Secure logging — never log PII
- Parameterized queries only (no string concatenation in SQL)

### Structure
- Controllers: thin, delegate to services, return appropriate HTTP status codes
- Services: business logic, injected via interfaces
- Models: request/response DTOs, separate from domain entities
- Data: DbContext, repositories with interfaces
- Infrastructure: custom exceptions, middleware, extension methods

## Example

```csharp
public class UserService : IUserService
{
    private readonly IUserRepository _userRepository;
    private readonly ILogger<UserService> _logger;

    public UserService(IUserRepository userRepository, ILogger<UserService> logger)
    {
        _userRepository = userRepository;
        _logger = logger;
    }

    public async Task<UserResponse> GetByIdAsync(int id)
    {
        ArgumentOutOfRangeException.ThrowIfNegativeOrZero(id);

        var user = await _userRepository.GetByIdAsync(id);
        if (user is null)
        {
            throw new NotFoundException($"User with ID {id} not found.");
        }

        _logger.LogInformation("Retrieved user {UserId}", id);
        return MapToResponse(user);
    }
}
```

## Dependency Injection Wiring

After writing production code, register all new services and repositories in `Program.cs`:

1. Scan the code you wrote for all interfaces and implementations
2. Register with appropriate lifetimes:
   - **Scoped** (default): services, repositories, DbContext
   - **Singleton**: configuration objects, HTTP clients (via `AddHttpClient`)
   - **Transient**: lightweight stateless utilities

```csharp
// Services
builder.Services.AddScoped<IUserService, UserService>();
builder.Services.AddScoped<IOrderService, OrderService>();

// Repositories
builder.Services.AddScoped<IUserRepository, UserRepository>();

// Database
builder.Services.AddDbContext<AppDbContext>(options =>
    options.UseSqlServer(builder.Configuration.GetConnectionString("DefaultConnection")));

// External HTTP clients
builder.Services.AddHttpClient<IExternalApiClient, ExternalApiClient>();
```

## Boundary

- Production code + DI wiring ONLY
- Do NOT write tests (use `/test` for that)
- Do NOT write documentation (use `/docs` for that)
