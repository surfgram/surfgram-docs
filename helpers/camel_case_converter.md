# CamelCaseConverter

Internal string conversion utility (snake_case → CamelCase)

## Behavior

| Input (snake_case) | Output (CamelCase) |
|--------------------|--------------------|
| `user_name`        | `userName`         |
| `api_endpoint`     | `apiEndpoint`      |
| `id`              | `id`               |

## Internal Usage Only

- Used by framework's serialization system
- Processes internal field names
- Not for application-level string conversion

> Note: This is an internal component. Use public API methods for case conversion needs.