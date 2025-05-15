# Token

## Package
```python
from surfgram.exceptions import TokenError
from surfgram.core.validator.token import Token
```

> **INTERNAL COMPONENT WARNING**  
> This class is an internal implementation detail of the Surfgram framework.  
> Client code should not instantiate or interact with this class directly.  
> Use the public `Bot` interface instead.

## Class Description
The `Token` class provides strict validation and encapsulation for Telegram bot tokens, ensuring only properly formatted tokens are used within the framework.

## Token Format Specification
Valid tokens must conform to the following regex pattern:
```python
r"^\d{1,10}:[A-Za-z0-9_-]{35,}$"
```

This enforces:
- 1-10 digit bot ID prefix
- Colon separator
- 35+ character alphanumeric secret (including `_` and `-`)

## Constructor
```python
__init__(token: str) -> None
```

### Parameters
| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `token`   | str  | Yes      | Raw bot token string |

### Raises
| Exception | Condition |
|-----------|-----------|
| `TokenError` | When token fails format validation |

## Public Methods

### Validation
```python
validate() -> None
```

#### Description
Performs strict format validation of the contained token.

#### Behavior
- Uses compiled regex pattern for efficient validation
- Raises `TokenError` with descriptive message on failure
- Automatically called during initialization

#### Example Failure Case
```python
Token("invalid!token")  # Raises TokenError immediately
```

### String Conversion
```python
__str__() -> str
```

#### Description
Provides safe access to the validated token string.

#### Returns
| Type | Description |
|------|-------------|
| str  | The validated token string |

#### Usage
```python
valid_token = Token("12345:validtokenstring")
print(str(valid_token))  # "12345:validtokenstring"
```
