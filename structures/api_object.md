# APIObject

## Package
```python
from surfgram import APIObject
```

## Class Description
The `APIObject` class provides dynamic attribute access to Telegram Bot API responses, converting JSON structures into Python objects with intelligent error handling.

> **Framework Implementation Detail**  
> While users interact with APIObject instances through handler callbacks, they should typically use standard attribute access rather than direct class interaction.

## Constructor
```python
__init__(data: Dict[str, Any]) -> None
```

### Parameters
| Parameter | Type | Description |
|-----------|------|-------------|
| `data` | Dict[str, Any] | Raw API response dictionary |

## Core Functionality

### Dynamic Attribute Access
```python
__getattr__(item: str) -> Any
```

#### Behavior
1. Attempts to retrieve the requested attribute from API response data
2. Automatically wraps nested dictionaries as `APIObject` instances
3. Provides fuzzy-matched suggestions for invalid attributes

#### Response Handling
| Input Type | Return Type |
|------------|-------------|
| Primitive (str, int, etc.) | Direct value |
| Dictionary | New `APIObject` instance |
| List | Raw list (no conversion) |

#### Error Handling
Raises `AttributeError` with suggestions when:
- Attribute doesn't exist in response data
- Attribute exists but value is `None` (Telegram API convention)

### String Representation
```python
__repr__() -> str
```
Returns evaluable string representation including class name and source data.

## Usage in Framework

### Handler Implementation Example
```python
from surfgram.types import BotCommand
from typing import Callable

class CmdHandler(BotCommand):
    @property
    def __names__(self):
        return ["start", "help"]
    
    @property
    def __callback__(self) -> Callable:
        return self.handle
    
    async def handle(self, update: APIObject, bot):
        chat = update.message.chat
        
        await bot.send_message(
            chat_id=chat.id,
            text=f"Hello {user.first_name}!"
        )
```
