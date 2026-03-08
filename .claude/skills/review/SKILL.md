# Review Code

---
context: fork
agent: general-purpose
model: claude-opus-4-6
allowed-tools: Read, Glob, Grep
---

## Purpose

Review code, tests, and documentation against guard rails and best practices. This skill runs AFTER `/dev-implement` and `/test`, and BEFORE `/docs`.

## References

Read ALL of these:
- `.claude/guard-rails.md`
- `.claude/context/ms-dotnet-patterns.md`
- `.claude/context/azure-best-practices.md`
- `.claude/context/naming-conventions.md`
- `.claude/context/security-standards.md`
- `.claude/context/common-libraries.md`

## Review Checklist

### Code Quality
- [ ] .NET 9, C# — no deprecated APIs
- [ ] Async/await used for all I/O operations
- [ ] Constructor-based dependency injection (no `new` for services)
- [ ] PascalCase for classes/methods, camelCase for variables
- [ ] Single responsibility per class and method
- [ ] No magic numbers or hardcoded strings (use constants/config)
- [ ] No dead code, commented-out code, or TODO hacks

### Security
- [ ] NO hardcoded secrets, connection strings, or API keys
- [ ] Input validation on all public endpoints
- [ ] Authentication/authorization attributes present
- [ ] Secure logging — no PII, passwords, or tokens logged
- [ ] CORS configured appropriately
- [ ] SQL injection prevention (parameterized queries only)

### Testing
- [ ] >80% code coverage
- [ ] All public methods have unit tests
- [ ] Edge cases tested (null, empty, boundary values)
- [ ] Error scenarios tested (exceptions, failures)
- [ ] Integration tests for API endpoints
- [ ] AAA pattern followed
- [ ] Mocking used correctly (no over-mocking)

### Documentation
- [ ] Technical design reflects current architecture
- [ ] All endpoints documented in `api-{endpoint}.md`
- [ ] No stale or outdated documentation

### Architecture
- [ ] Repository pattern for data access
- [ ] Proper separation of concerns (Controller → Service → Repository)
- [ ] Interfaces defined for all services and repositories
- [ ] DI registrations use correct lifetimes (Scoped/Singleton/Transient)

## Output Format

Report findings as:

```
## Review Results

### PASS
- [list of items that pass]

### ISSUES (must fix)
- [critical issues that violate guard rails]

### SUGGESTIONS (nice to have)
- [improvements that would enhance quality]
```

## Boundary

- READ-ONLY — do NOT modify any files
- Report findings back to the user
- Flag any guard rail violations as blocking issues
