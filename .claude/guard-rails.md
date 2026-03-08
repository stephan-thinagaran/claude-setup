# Guard Rails

## Code Standards

- [ ] .NET 9 (current stable, no older versions)
- [ ] Async/await for all I/O operations
- [ ] Dependency injection mandatory (constructor injection)
- [ ] Naming: PascalCase for classes/methods, camelCase for variables
- [ ] Single responsibility per method
- [ ] No magic numbers (use constants/config)
- [ ] Testable code (no static dependencies)

## Security

- [ ] NO hardcoded secrets (use Azure Key Vault)
- [ ] Input validation on all endpoints
- [ ] Proper authentication/authorization
- [ ] Secure logging (never log PII)
- [ ] CORS properly configured
- [ ] SQL injection prevention (parameterized queries)

## Testing

- [ ] Minimum 80% code coverage
- [ ] All public methods have unit tests
- [ ] Edge cases and error scenarios tested
- [ ] Integration tests for API endpoints
- [ ] xUnit framework
- [ ] AAA pattern (Arrange-Act-Assert)
- [ ] Mocking used for dependencies

## Documentation

- [ ] Technical design updated for architecture changes
- [ ] Every new endpoint documented in api-{endpoint}.md
- [ ] Implementation details included
- [ ] Security considerations documented
- [ ] No outdated/stale documentation

## Azure/Microsoft Standards

- [ ] Use Azure Key Vault for secrets
- [ ] Use Azure SQL or Cosmos DB for data
- [ ] Use managed identity for auth
- [ ] Use Application Insights for monitoring
- [ ] Infrastructure handled by separate team (Bicep/ARM)

## Skill Workflow Enforcement

Skills must be run in order: `/dev-scaffold` → `/dev-implement` → `/test` → `/review` → `/docs`

- `/review` runs AFTER code and tests are written
- `/docs` runs AFTER review passes
- Each skill respects its boundary (e.g., `/test` does not modify production code)
