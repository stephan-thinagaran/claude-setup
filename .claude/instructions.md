# Claude Code Instructions

## Overview
Generic, reusable template for MS/Azure microservices using .NET 9, async/await, dependency injection, and xUnit tests.

---

## Skills (Sequential Workflow)

**`/dev-scaffold`** → Create microservice structure
**`/dev-implement`** → Write production code + wire DI
**`/test`** → Write tests + coverage analysis (>80% target)
**`/review`** → Review code & security
**`/docs`** → Update documentation

Each skill runs in an isolated context (`context: fork`) and reads:
- `guard-rails.md` (standards)
- Relevant context files
- Existing code/docs

---

## How to Invoke

Sequential workflow for a new feature:

```
1. /dev-scaffold MyService         → creates folder structure + boilerplate
2. /dev-implement [feature]        → writes production code + wires DI
3. /test [feature]                 → writes unit + integration tests + coverage analysis
4. /review                         → reviews code, tests, security
5. /docs                           → updates technical-design.md and API docs
```

For existing services, skip `/dev-scaffold` and start at `/dev-implement`.

---

## Folder Structure

```
.claude/
├── instructions.md (this file)
├── guard-rails.md
├── skills/ (5 skill folders with SKILL.md)
├── context/ (fill with team-specific standards)
├── config/ (MCP server configuration)
└── templates/ (reusable starters, fill as needed)

docs/
├── {microservice-name}/
│   ├── technical-design.md
│   └── api-{endpoint-name}.md

src/ + tests/ → Standard .NET structure
```

---

## Key Principles

- All code: async/await, dependency injection, testable
- Security: NO hardcoded secrets, use Azure Key Vault
- Tests: >80% coverage minimum
- Docs: Update with every code change
- Guard rails are non-negotiable

---

## Guard Rails (Quick Reference)

**Code:**
- .NET 9 only
- Async/await mandatory
- Dependency injection required
- Clear naming (PascalCase classes, camelCase variables)
- Single responsibility per method

**Security:**
- NO hardcoded secrets
- Input validation
- Proper auth/authorization
- Secure logging (no PII)

**Testing:**
- Minimum 80% coverage
- Unit + integration tests
- Edge cases covered
- xUnit + AAA pattern

**Documentation:**
- Technical design updated
- Every endpoint documented
- Implementation details included

---

## Context Files (Fill with Team Standards)

- `ms-dotnet-patterns.md` — .NET patterns and conventions
- `azure-best-practices.md` — Azure service configuration
- `naming-conventions.md` — naming rules for your team
- `security-standards.md` — auth, data protection, compliance
- `common-libraries.md` — approved NuGet packages
- `microservices-patterns.md` — service communication patterns

---

## Templates (Fill as Needed)

- appsettings.template.json
- Program.cs.template
- .gitignore.template
- .editorconfig.template
- (add more as needed)

---

## First Use

1. Clone repo
2. `/dev-scaffold MyService` — creates structure + boilerplate + .sln
3. Create `docs/MyService/technical-design.md` with your design
4. `/dev-implement [first feature]`
5. `/test [first feature]`
6. `/review`
8. `/docs`
9. Commit to git

Done!
