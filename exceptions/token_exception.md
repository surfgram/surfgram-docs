# TokenError

Internal exception for bot token validation failures

## Usage
```python
raise TokenError("Invalid token format")
```

## Behavior
- Inherits from base `Exception` class
- Carries simple error message
- Used internally by `Token` validator class

## When Thrown
- Invalid token format (regex mismatch)
- Missing token configuration
- Token-related API errors

> Note: This is an internal error type. Handle at configuration level.