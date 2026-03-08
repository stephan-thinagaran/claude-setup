# Naming Conventions

Fill this file with your team's naming standards. Example structure:

## C# Naming

| Element | Convention | Example |
|---------|-----------|---------|
| Class | PascalCase | `UserService` |
| Interface | IPascalCase | `IUserService` |
| Method | PascalCase | `GetByIdAsync` |
| Property | PascalCase | `FirstName` |
| Parameter | camelCase | `userId` |
| Local variable | camelCase | `userCount` |
| Private field | _camelCase | `_userRepository` |
| Constant | PascalCase | `MaxRetryCount` |
| Enum | PascalCase | `UserStatus.Active` |

## File Naming
- One class per file
- File name matches class name: `UserService.cs`
- Test files: `UserServiceTests.cs`
- Interfaces: `IUserService.cs`

## Project Naming
- Source: `{ServiceName}` (e.g., `UserService`)
- Tests: `{ServiceName}.Tests` (e.g., `UserService.Tests`)

## Async Methods
- Suffix with `Async`: `GetByIdAsync`, `SaveChangesAsync`
- Exception: event handlers and test methods
