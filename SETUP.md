# Setup

## Prerequisites

- .NET 10 SDK installed
- Git configured
- Claude Code or Claude AI access
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
3. `.claude/instructions.md` - How to use Claude Code

### 3. Create Your Microservice

```bash
# Create source folder
mkdir -p src/YourService/Controllers
mkdir -p src/YourService/Services
mkdir -p src/YourService/Models
mkdir -p src/YourService/Data
mkdir -p src/YourService/Infrastructure

# Create test folder
mkdir -p tests/YourService.Tests/UnitTests
mkdir -p tests/YourService.Tests/IntegrationTests

# Create documentation folder
mkdir -p docs/YourService
```

### 4. Create Technical Design

Create `docs/YourService/technical-design.md` with:
- Microservice purpose
- Key responsibilities
- Architecture approach
- Data model overview
- External dependencies

### 5. Use Claude Code

Invoke agents in sequence:

```
Developer Agent: Implement [feature]
Test Agent: Write tests for [feature]
Review Agent: Review code and tests
Documentation Agent: Update technical design and API docs
```

## File Structure Example

After setup, your project looks like:

```
claude-code-ms-azure-template/
├── .claude/                    ← Claude Code config (don't modify)
│   ├── instructions.md
│   ├── guard-rails.md
│   ├── sub-agents/
│   ├── context/
│   └── templates/
│
├── docs/
│   └── YourService/
│       ├── technical-design.md
│       ├── api-endpoint-1.md
│       └── api-endpoint-2.md
│
├── src/
│   ├── YourService/
│   │   ├── YourService.csproj
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
│   ├── YourService.Tests/
│   │   ├── UnitTests/
│   │   └── IntegrationTests/
│   │
│   └── AnotherService.Tests/
│
├── README.md
├── ARCHITECTURE.md
├── SETUP.md
└── .gitignore
```

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

Use `.claude/templates/Program.cs.template` (when available) as starting point:
- Configure dependency injection
- Register services
- Configure middleware
- Setup logging

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
2. "Developer Agent: Implement [feature] endpoint"
3. "Test Agent: Write tests for [feature]"
4. "Review Agent: Review code and tests"
5. "Documentation Agent: Update technical-design.md and create api-[feature].md"
6. `git commit` with clear message

## Troubleshooting

**Code rejected by Review Agent?**
- Check `.claude/guard-rails.md`
- Review examples in `.claude/sub-agents/developer-agent/examples/`
- Verify async/await, DI, error handling

**Test coverage below 80%?**
- Check which methods aren't tested
- Add tests for edge cases and errors
- Review test examples in `.claude/sub-agents/test-agent/examples/`

**Don't know which pattern to use?**
- Check `.claude/context/ms-dotnet-patterns.md` (to be filled)
- Look at existing microservices in `src/`
- Ask in documentation or code comments

## Next Steps

1. Create your first microservice folder structure
2. Write technical design document
3. Start implementing features with agents
4. Commit to git
5. Fill context files and templates as you discover patterns
