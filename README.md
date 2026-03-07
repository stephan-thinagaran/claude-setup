# Claude Code MS/Azure Template

A generic, reusable Claude Code template for building .NET 10 microservices on Microsoft Azure.

## What Is This?

This is a pre-configured template with:
- **4 AI Agents** (Developer, Test, Review, Documentation)
- **Guard Rails** (standards and best practices)
- **Folder Structure** (organized, scalable)
- **Context Files** (knowledge base, to be filled)
- **Templates** (reusable starters, to be filled)

Clone this repo as a starting point for any new microservice project.

## Quick Start

1. Clone this repo
2. Read `.claude/instructions.md`
3. Create your microservice folder in `src/`
4. Create technical design in `docs/{service}/`
5. Invoke agents: Developer → Test → Review → Documentation

## Agents

| Agent | Role |
|-------|------|
| Developer Agent | Write production code |
| Test Agent | Write tests (>80% coverage) |
| Review Agent | Review for quality & security |
| Documentation Agent | Update technical design & API docs |

See `.claude/sub-agents/` for detailed instructions for each agent.

## Folder Structure

```
.claude/          → Claude Code configuration
docs/             → Technical design + API documentation
src/              → Microservices source code
tests/            → Unit and integration tests
```

## Guard Rails

All code must follow standards in `.claude/guard-rails.md`:
- .NET 10+ only
- Async/await mandatory
- Dependency injection required
- No hardcoded secrets
- >80% test coverage
- Clear documentation

## Getting Started

Read these files in order:
1. `.claude/instructions.md` - Master guide
2. `.claude/guard-rails.md` - Standards
3. `.claude/sub-agents/{agent}/agent.md` - Agent instructions

Then start using it!

## Context Files (To Fill)

- `ms-dotnet-patterns.md`
- `azure-best-practices.md`
- `naming-conventions.md`
- `security-standards.md`
- `common-libraries.md`
- `microservices-patterns.md`

## Templates (To Fill)

- `appsettings.template.json`
- `Program.cs.template`
- `.gitignore.template`
- `.editorconfig.template`

## License

MIT
