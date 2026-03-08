# Write Documentation

---
context: fork
agent: general-purpose
model: claude-sonnet-4-6
allowed-tools: Write, Edit, Read, Glob, Grep
---

## Purpose

Create and update technical design and API documentation. This skill runs AFTER `/review` confirms the code is ready.

## References

Read these before starting:
- `.claude/guard-rails.md`
- The production code and tests being documented

## What to Create/Update

### technical-design.md (`docs/{ServiceName}/technical-design.md`)

Update with:
- Service purpose and responsibilities
- Architecture overview (components and their interactions)
- Data model (entities, relationships)
- External dependencies (other services, databases, external APIs)
- Security considerations
- Error handling approach

### API Documentation (`docs/{ServiceName}/api-{endpoint}.md`)

Create one file per endpoint group with:

```markdown
# API: {Endpoint Name}

## Functional Requirement
What this endpoint does and why it exists.

## Endpoints

### {HTTP Method} {Route}

**Parameters:**
| Name | Type | Location | Required | Description |
|------|------|----------|----------|-------------|

**Request Body:** (if applicable)
```json
{ "example": "value" }
```

**Response:** (status code + body)
```json
{ "example": "value" }
```

**Error Responses:**
| Status | Description |
|--------|-------------|

## Security
- Authentication: [required/optional]
- Authorization: [roles/policies]

## Implementation Notes
- Key design decisions
- Performance considerations
```

## Boundary

- Documentation ONLY
- Do NOT modify production code or tests
- Place all docs in `docs/{ServiceName}/`
- Keep docs concise and accurate — no filler text
