# Common Libraries

Fill this file with your team's approved NuGet packages. Example structure:

## Core Framework
| Package | Purpose | Version |
|---------|---------|---------|
| Microsoft.AspNetCore.* | Web API framework | 9.x |
| Microsoft.EntityFrameworkCore | ORM / data access | 9.x |
| Microsoft.Extensions.DependencyInjection | DI container | 9.x |

## Testing
| Package | Purpose | Version |
|---------|---------|---------|
| xunit | Test framework | latest |
| Moq | Mocking library | latest |
| Microsoft.AspNetCore.Mvc.Testing | Integration test host | 9.x |
| coverlet.collector | Code coverage | latest |

## Azure
| Package | Purpose | Version |
|---------|---------|---------|
| Azure.Identity | Managed identity auth | latest |
| Azure.Extensions.AspNetCore.Configuration.Secrets | Key Vault config | latest |
| Microsoft.ApplicationInsights.AspNetCore | Telemetry | latest |

## Validation
| Package | Purpose | Version |
|---------|---------|---------|
| FluentValidation.AspNetCore | Input validation | latest |

## Serialization
| Package | Purpose | Version |
|---------|---------|---------|
| System.Text.Json | JSON (built-in, preferred) | — |

## Packages to Avoid
- Newtonsoft.Json (use System.Text.Json unless compatibility required)
- AutoMapper (prefer manual mapping for transparency)
