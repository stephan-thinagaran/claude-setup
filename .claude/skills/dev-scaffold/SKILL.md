# Scaffold Microservice

---
context: fork
agent: general-purpose
model: claude-haiku-4-5-20251001
allowed-tools: Write, Bash, Read, Glob
---

## Purpose

Create the folder structure and boilerplate files for a new .NET 9 microservice.

## References

Read these before starting:
- `.claude/guard-rails.md`
- `.claude/context/ms-dotnet-patterns.md`
- `.claude/context/naming-conventions.md`

## What to Create

Given a microservice name (e.g., `UserService`), create:

```
src/{ServiceName}/
├── {ServiceName}.csproj
├── Program.cs
├── appsettings.json
├── appsettings.Development.json
├── Controllers/
├── Services/
├── Models/
├── Data/
└── Infrastructure/

tests/{ServiceName}.Tests/
├── {ServiceName}.Tests.csproj
├── UnitTests/
└── IntegrationTests/

docs/{ServiceName}/
└── technical-design.md (empty template)
```

## Boilerplate Requirements

### {ServiceName}.csproj
- Target `net9.0`
- Include standard Microsoft.AspNetCore packages

### Program.cs
- Minimal hosting model
- DI container setup (empty, ready for registrations)
- Standard middleware pipeline (HTTPS redirection, authorization, controllers)
- Application Insights configuration placeholder

### appsettings.json
- Logging configuration
- Connection string placeholders
- Azure Key Vault placeholder

### Test .csproj
- Reference main project
- Include xUnit, Moq, Microsoft.AspNetCore.Mvc.Testing packages

### Solution File
- If a `.sln` file exists at the repo root, add the new projects to it
- If no `.sln` exists, create one and add the projects

## Boundary

- Structure and boilerplate ONLY
- Do NOT write business logic, controllers, services, or models
- Do NOT write tests
- Keep Program.cs minimal with DI ready for `/dev-implement` to add registrations
