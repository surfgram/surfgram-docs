# SwitchInlineQueryChosenChat

Telegram Bot API SwitchInlineQueryChosenChat type

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
from surfgram.types import SwitchInlineQueryChosenChat

class MySwitchInlineQueryChosenChatHandler(SwitchInlineQueryChosenChat):    
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
| `query` | `str` | Optional. The default inline query to be inserted in the input field. If left empty, only the bot's username will be inserted |
| `allow_user_chats` | `bool` | Optional. True, if private chats with users can be chosen |
| `allow_bot_chats` | `bool` | Optional. True, if private chats with bots can be chosen |
| `allow_group_chats` | `bool` | Optional. True, if group and supergroup chats can be chosen |
| `allow_channel_chats` | `bool` | Optional. True, if channel chats can be chosen |

## Best Practices

1. **Naming**: 
   - Use descriptive class names (`PaymentHandler` vs `Handler1`)
   - Prefix related handlers (`AdminCommands`, `UserCommands`)
