# Security Standards

Fill this file with your team's security requirements. Example structure:

## Authentication
- JWT bearer tokens for API authentication
- Azure AD / Entra ID integration
- Token validation middleware

## Authorization
- Role-based access control (RBAC)
- Policy-based authorization for complex rules
- `[Authorize]` attribute on all endpoints (opt-out, not opt-in)

## Secrets Management
- ALL secrets in Azure Key Vault
- Never in code, appsettings, or environment variables in production
- Use `DefaultAzureCredential` for local development

## Input Validation
- Data annotations on all request models
- FluentValidation for complex rules
- Validate at controller level before processing

## Data Protection
- Encrypt sensitive data at rest
- TLS for all communication
- Never log PII (names, emails, SSNs, tokens)

## CORS
- Restrict to known origins
- No wildcard (`*`) in production

## SQL Injection Prevention
- Parameterized queries only
- Use Entity Framework (never raw string concatenation)
