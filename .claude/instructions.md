# Claude Code Instructions

## Overview
Generic, reusable template for MS/Azure microservices using .NET 10, async/await, dependency injection, and xUnit tests.

---

## Four Agents (Sequential Workflow)

**Developer Agent** → Write code  
**Test Agent** → Write tests (>80% coverage)  
**Review Agent** → Review code & security  
**Documentation Agent** → Update docs  

Each agent reads:
- `guard-rails.md` (standards)
- Relevant context files
- Existing code/docs

---

## How to Invoke

Manual, sequential:

```
1. "Developer Agent: [task description]"
2. "Test Agent: Write tests for above"
3. "Review Agent: Review code and tests"
4. "Documentation Agent: Update technical-design.md and api docs"
```

---

## Folder Structure

```
.claude/
├── instructions.md (this file)
├── guard-rails.md
├── sub-agents/ (4 agent folders with agent.md)
├── context/ (empty, fill as needed)
└── templates/ (empty, fill as needed)

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
- .NET 10+ only
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

## Context Files (Empty, Fill Later)

- ms-dotnet-patterns.md
- azure-best-practices.md
- naming-conventions.md
- security-standards.md
- common-libraries.md
- microservices-patterns.md

---

## Templates (Empty, Fill Later)

- appsettings.template.json
- Program.cs.template
- .gitignore.template
- .editorconfig.template
- (add more as needed)

---

## First Use

1. Clone repo
2. Create microservice folder in src/
3. Create technical-design.md in docs/{service}/
4. Invoke Developer Agent
5. Invoke Test Agent
6. Invoke Review Agent
7. Invoke Documentation Agent
8. Commit to git

Done!
