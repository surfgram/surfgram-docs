# SnakeCaseConverter

Internal string conversion utility to snake_case format

## Behavior

| Input            | Output         |
|------------------|----------------|
| `UserName`       | `user_name`    |
| `APIEndpoint`    | `apiendpoint`  |
| `someValue`      | `somevalue`    |

## Internal Usage Only
- Used by framework's serialization system
- Processes internal field names
- Converts strings to lowercase with underscore separation
- Simple space-to-underscore conversion (does not handle complex camelCase)

> Note: This is an internal component. Use framework's public utilities for application-level string conversion needs.