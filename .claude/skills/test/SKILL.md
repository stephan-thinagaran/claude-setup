# Write Tests

---
context: fork
agent: general-purpose
model: claude-sonnet-4-6
allowed-tools: Write, Edit, Read, Glob, Grep, Bash
---

## Purpose

Write comprehensive xUnit unit and integration tests targeting >80% code coverage.

## References

Read these before starting:
- `.claude/guard-rails.md`
- `.claude/context/common-libraries.md`
- The production code being tested

## Standards

### Framework & Libraries
- xUnit (test framework)
- Moq (mocking)
- FluentAssertions (optional, if already in use)
- Microsoft.AspNetCore.Mvc.Testing (integration tests)

### Patterns
- **AAA Pattern**: Arrange, Act, Assert — clearly separated with comments
- **One assertion per concept** (multiple related asserts are OK)
- **Descriptive test names**: `MethodName_Scenario_ExpectedResult`
- **Test classes mirror production classes**: `UserService` → `UserServiceTests`

### Unit Tests
- Mock all dependencies using Moq
- Test happy path, edge cases, and error scenarios
- Test input validation
- Test null/empty/boundary values

### Integration Tests
- Use WebApplicationFactory for API endpoint tests
- Use in-memory database for data tests
- Test full request/response cycle
- Test authentication/authorization

## Example

```csharp
public class UserServiceTests
{
    private readonly Mock<IUserRepository> _mockRepo;
    private readonly Mock<ILogger<UserService>> _mockLogger;
    private readonly UserService _sut;

    public UserServiceTests()
    {
        _mockRepo = new Mock<IUserRepository>();
        _mockLogger = new Mock<ILogger<UserService>>();
        _sut = new UserService(_mockRepo.Object, _mockLogger.Object);
    }

    [Fact]
    public async Task GetByIdAsync_ValidId_ReturnsUser()
    {
        // Arrange
        var expectedUser = new User { Id = 1, Name = "Test" };
        _mockRepo.Setup(r => r.GetByIdAsync(1))
            .ReturnsAsync(expectedUser);

        // Act
        var result = await _sut.GetByIdAsync(1);

        // Assert
        Assert.NotNull(result);
        Assert.Equal("Test", result.Name);
    }

    [Fact]
    public async Task GetByIdAsync_InvalidId_ThrowsArgumentException()
    {
        // Arrange & Act & Assert
        await Assert.ThrowsAsync<ArgumentOutOfRangeException>(
            () => _sut.GetByIdAsync(0));
    }

    [Fact]
    public async Task GetByIdAsync_NotFound_ThrowsNotFoundException()
    {
        // Arrange
        _mockRepo.Setup(r => r.GetByIdAsync(It.IsAny<int>()))
            .ReturnsAsync((User?)null);

        // Act & Assert
        await Assert.ThrowsAsync<NotFoundException>(
            () => _sut.GetByIdAsync(1));
    }
}
```

## Coverage Analysis

After writing tests, analyze and fill coverage gaps:

1. **Run tests with coverage collection:**
   ```bash
   dotnet test --collect:"XPlat Code Coverage" --results-directory ./TestResults
   ```

2. **Analyze coverage report** to identify:
   - Classes with <80% coverage
   - Untested public methods
   - Untested branches (if/else, switch, try/catch)
   - Missing edge case tests

3. **Fill gaps** — prioritize by risk (security-critical code first):
   - Write missing tests using the same patterns above
   - Re-run coverage to verify >80% target is met

## Boundary

- Test code ONLY (including coverage analysis)
- Do NOT modify production code
- Do NOT write documentation
- Place unit tests in `tests/{ServiceName}.Tests/UnitTests/`
- Place integration tests in `tests/{ServiceName}.Tests/IntegrationTests/`
