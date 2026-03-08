# Claude Code MS/Azure Template

A generic, reusable Claude Code template for building .NET 9 microservices on Microsoft Azure.

## What Is This?

This is a pre-configured template with:
- **5 Claude Code Skills** (scaffold, implement, test, review, docs)
- **Guard Rails** (standards and best practices)
- **Folder Structure** (organized, scalable)
- **Context Files** (knowledge base, to be filled)
- **Templates** (reusable starters, to be filled)

Clone this repo as a starting point for any new microservice project.

## Quick Start

1. Clone this repo
2. Read `.claude/instructions.md`
3. `/dev-scaffold MyService` — creates structure + boilerplate
4. Create technical design in `docs/MyService/`
5. Implement: `/dev-implement` → `/test` → `/review` → `/docs`

## Skills

| Skill | Purpose |
|-------|---------|
| `/dev-scaffold` | Create microservice folder structure + boilerplate |
| `/dev-implement` | Write production C# code + wire DI |
| `/test` | Write xUnit unit + integration tests + coverage analysis |
| `/review` | Review code for quality, security, guard rails |
| `/docs` | Create/update technical design + API docs |

See `.claude/skills/` for detailed instructions for each skill.

## Folder Structure

```
.claude/          → Claude Code configuration + skills
docs/             → Technical design + API documentation
src/              → Microservices source code
tests/            → Unit and integration tests
```

## Guard Rails

All code must follow standards in `.claude/guard-rails.md`:
- .NET 9
- Async/await mandatory
- Dependency injection required
- No hardcoded secrets
- >80% test coverage
- Clear documentation

## Getting Started

Read these files in order:
1. `.claude/instructions.md` - Master guide
2. `.claude/guard-rails.md` - Standards
3. `.claude/skills/{skill}/SKILL.md` - Skill instructions

Then start using it!

## Context Files (To Fill)

These are team-specific — fill with your standards:
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
