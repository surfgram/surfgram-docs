# BaseConfig

## Package
```python
from surfgram import configs
```

## Class Description
The `BaseConfig` class defines the essential configuration interface for bots. All concrete configuration implementations must inherit from this class.

## Configuration Requirements
Subclasses must define:
1. `__bot_token__`: Valid Telegram bot token string
2. `__listener__` (optional): Configured event listener instance

## Public Interface

### Class Attributes

#### `__bot_token__: str`
**Description**:  
Stores the bot's authentication token. Must be set by concrete implementations.

**Requirements**:
- Must match Telegram's token format
- Should be kept secret
- Must be set before bot initialization

**Example**:
```python
class MyConfig(configs.BaseConfig):
    __bot_token__ = "12345:validtokenstring"
```

#### `__listener__: Optional[Listener]` 
**Description**:  
Stores the configured event listener instance.

**Default**: `None`

**Usage Notes**:
- Required for bots using the `listen()` method
- Must implement the `Listener` protocol
- Can be `None` for send-only bots

### Methods

#### `get_token() -> str`

**Description**:  
Safe accessor for the bot token.

**Returns**:
| Type | Description |
|------|-------------|
| `str` | Validated bot token string |

**Usage**:
```python
token = MyConfig.get_token()
```

#### `get_listener() -> Optional[Listener]`

**Description**:  
Retrieves the configured event listener.

**Returns**:
| Type | Description |
|------|-------------|
| `Optional[Listener]` | Listener instance or None |


## Example
```python
from surfgram import configs
from surfgram import listeners

class Config(configs.BaseConfig):
    __bot_token__ = "12345:productiontoken"
    __listener__ = listeners.BaseListener
```
