# CallbackQuery

Telegram Bot API CallbackQuery type

## Overview

| Property        | Type               | Required | Default | Description                              |
|-----------------|--------------------|----------|---------|------------------------------------------|
| `__is_active__` | `bool`             | No       | `True`  | Global handler switch                   |
| `__names__`     | `List[str]`        | No       | `[]`    | Trigger filter (empty = all)            |
| `__callback__`  | `Callable`         | **Yes**  | -       | Async handler function                  |

## Implementation Guide

### Basic Template

```python
from typing import List, Callable
from surfgram.types import CallbackQuery

class MyCallbackQueryHandler(CallbackQuery):    
    @property
    def __is_active__(self) -> bool:
        return True  # Set False to disable
        
    @property
    def __names__(self) -> List[str]:
        return []  # ['specific_trigger'] for filtered handling
        
    @property
    def __callback__(self) -> Callable:
        return self.process_event
        
    async def process_event(self, update: dict, bot) -> None:
        """Main handler logic"""
        # Implement your processing here
```

### Field Reference

The update object contains these fields:

| Field          | Type              | Description                     |
|----------------|-------------------|---------------------------------|
| `id` | `str` | Unique identifier for this query |
| `from` | `User` | Sender |
| `message` | `MaybeInaccessibleMessage` | Optional. Message sent by the bot with the callback button that originated the query |
| `inline_message_id` | `str` | Optional. Identifier of the message sent via the bot in inline mode, that originated the query. |
| `chat_instance` | `str` | Global identifier, uniquely corresponding to the chat to which the message with the callback button was sent. Useful for high scores in games. |
| `data` | `str` | Optional. Data associated with the callback button. Be aware that the message originated the query can contain no callback buttons with this data. |
| `game_short_name` | `str` | Optional. Short name of a Game to be returned, serves as the unique identifier for the game |

## Best Practices

1. **Naming**: 
   - Use descriptive class names (`PaymentHandler` vs `Handler1`)
   - Prefix related handlers (`AdminCommands`, `UserCommands`)
