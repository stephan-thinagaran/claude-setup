# MS/.NET Patterns

Fill this file with your team's .NET patterns and conventions. Example structure:

## API Controller Pattern
```csharp
// Example: thin controller delegating to service
[ApiController]
[Route("api/[controller]")]
public class UsersController : ControllerBase
{
    private readonly IUserService _userService;
    public UsersController(IUserService userService) => _userService = userService;

    [HttpGet("{id}")]
    public async Task<ActionResult<UserResponse>> GetById(int id)
    {
        var user = await _userService.GetByIdAsync(id);
        return Ok(user);
    }
}
```

## Repository Pattern
```csharp
// Example: repository interface + implementation
public interface IUserRepository
{
    Task<User?> GetByIdAsync(int id);
    Task<IEnumerable<User>> GetAllAsync();
    Task AddAsync(User user);
}
```

## Service Layer Pattern
```csharp
// Example: service with DI, validation, logging
public class UserService : IUserService
{
    private readonly IUserRepository _repo;
    private readonly ILogger<UserService> _logger;
    // Constructor injection, async methods, guard clauses
}
```

## Error Handling
- Use custom exception types (NotFoundException, ValidationException)
- Global exception handler middleware
- Return appropriate HTTP status codes

## Configuration
- Options pattern for strongly-typed config
- Azure Key Vault for secrets
- Environment-specific appsettings files
