# KeyboardButtonRequestChat

Telegram Bot API KeyboardButtonRequestChat type

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
from surfgram.types import KeyboardButtonRequestChat

class MyKeyboardButtonRequestChatHandler(KeyboardButtonRequestChat):
    """"""
    
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
| `request_id` | `int` | Signed 32-bit identifier of the request, which will be received back in the ChatShared object. Must be unique within the message |
| `chat_is_channel` | `bool` | Pass True to request a channel chat, pass False to request a group or a supergroup chat. |
| `chat_is_forum` | `bool` | Optional. Pass True to request a forum supergroup, pass False to request a non-forum chat. If not specified, no additional restrictions are applied. |
| `chat_has_username` | `bool` | Optional. Pass True to request a supergroup or a channel with a username, pass False to request a chat without a username. If not specified, no additional restrictions are applied. |
| `chat_is_created` | `bool` | Optional. Pass True to request a chat owned by the user. Otherwise, no additional restrictions are applied. |
| `user_administrator_rights` | `Union[ChatAdministrat, Rights]` | Optional. A JSON-serialized object listing the required administrator rights of the user in the chat. The rights must be a superset of bot_administrator_rights. If not specified, no additional restrictions are applied. |
| `bot_administrator_rights` | `Union[ChatAdministrat, Rights]` | Optional. A JSON-serialized object listing the required administrator rights of the bot in the chat. The rights must be a subset of user_administrator_rights. If not specified, no additional restrictions are applied. |
| `bot_is_member` | `bool` | Optional. Pass True to request a chat with the bot as a member. Otherwise, no additional restrictions are applied. |
| `request_title` | `bool` | Optional. Pass True to request the chat's title |
| `request_username` | `bool` | Optional. Pass True to request the chat's username |
| `request_photo` | `bool` | Optional. Pass True to request the chat's photo |

## Best Practices

1. **Naming**: 
   - Use descriptive class names (`PaymentHandler` vs `Handler1`)
   - Prefix related handlers (`AdminCommands`, `UserCommands`)
