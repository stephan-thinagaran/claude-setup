# Setup

## Prerequisites

- .NET 9 SDK installed
- Git configured
- Claude Code CLI installed
- Text editor or IDE (VS Code, Visual Studio)

## Initial Setup

### 1. Clone the Template

```bash
git clone https://github.com/your-org/claude-code-ms-azure-template.git MyMicroservice
cd MyMicroservice
```

### 2. Read Documentation

In this order:
1. `README.md` - Overview
2. `ARCHITECTURE.md` - Technology stack and patterns
3. `.claude/instructions.md` - How to use Claude Code skills

### 3. Scaffold Your Microservice

Use the `/dev-scaffold` skill to create your microservice structure automatically:

```
/dev-scaffold UserService
```

This creates:
- `src/UserService/` with .csproj, Program.cs, appsettings.json, and folder structure
- `tests/UserService.Tests/` with test project and folders
- `docs/UserService/technical-design.md` template
- Creates or updates the `.sln` solution file

### 4. Create Technical Design

Edit `docs/UserService/technical-design.md` with:
- Microservice purpose
- Key responsibilities
- Architecture approach
- Data model overview
- External dependencies

### 5. Implement Features

Use skills in sequence:

```
/dev-implement Implement user CRUD endpoints
/test Write tests for user CRUD endpoints
/review
/docs
```

## File Structure Example

After setup, your project looks like:

```
claude-code-ms-azure-template/
├── .claude/                    ← Claude Code config
│   ├── instructions.md
│   ├── guard-rails.md
│   ├── skills/
│   ├── context/
│   ├── config/
│   └── templates/
│
├── docs/
│   └── UserService/
│       ├── technical-design.md
│       ├── api-users.md
│       └── api-auth.md
│
├── src/
│   ├── UserService/
│   │   ├── UserService.csproj
│   │   ├── Program.cs
│   │   ├── Controllers/
│   │   ├── Services/
│   │   ├── Models/
│   │   ├── Data/
│   │   └── Infrastructure/
│   │
│   └── AnotherService/
│
├── tests/
│   ├── UserService.Tests/
│   │   ├── UnitTests/
│   │   └── IntegrationTests/
│   │
│   └── AnotherService.Tests/
│
├── MyProject.sln
├── README.md
├── ARCHITECTURE.md
├── SETUP.md
└── .gitignore
```

## Solution File (.sln)

For multi-service repos, keep a `.sln` at the repo root. The `/dev-scaffold` skill manages this automatically. To manage manually:

```bash
dotnet new sln -n MyProject
dotnet sln add src/UserService/UserService.csproj
dotnet sln add tests/UserService.Tests/UserService.Tests.csproj
```

This enables `dotnet build` and `dotnet test` to work across all projects from the repo root.

## Configuration

### appsettings.json

Copy template from `.claude/templates/appsettings.template.json` (when available):

```json
{
  "Logging": {
    "LogLevel": {
      "Default": "Information"
    }
  },
  "ConnectionStrings": {
    "DefaultConnection": "Server=YOUR_SERVER;Database=YOUR_DB;..."
  }
}
```

### Program.cs

The `/dev-scaffold` skill generates a minimal Program.cs. The `/dev-implement` skill wires up DI registrations as part of implementation.

## Guard Rails Checklist

Before committing code:

- [ ] Code uses async/await
- [ ] Dependencies injected
- [ ] No hardcoded secrets
- [ ] Tests >80% coverage
- [ ] Documentation updated
- [ ] Follows naming conventions

See `.claude/guard-rails.md` for complete checklist.

## First Feature Development

1. Update `docs/YourService/technical-design.md` if needed
2. `/dev-implement [feature]`
3. `/test [feature]`
5. `/review`
6. `/docs`
7. `git commit` with clear message

## Troubleshooting

**Code rejected by `/review`?**
- Check `.claude/guard-rails.md`
- Verify async/await, DI, error handling
- Ensure no hardcoded secrets

**Test coverage below 80%?**
- Run `/test` again to analyze coverage gaps and fill them
- Add tests for edge cases and error scenarios

**Don't know which pattern to use?**
- Check `.claude/context/ms-dotnet-patterns.md` (fill with your patterns)
- Look at existing microservices in `src/`

## Next Steps

1. Scaffold your first microservice with `/dev-scaffold`
2. Write technical design document
3. Start implementing features with skills
4. Commit to git
5. Fill context files and templates as you discover patterns
