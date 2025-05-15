# User

Telegram Bot API User type

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
from surfgram.types import User

class MyUserHandler(User):
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
| `id` | `int` | Unique identifier for this user or bot. This number may have more than 32 significant bits and some programming languages may have difficulty/silent defects in interpreting it. But it has at most 52 significant bits, so a 64-bit integer or double-precision float type are safe for storing this identifier. |
| `is_bot` | `bool` | True, if this user is a bot |
| `first_name` | `str` | User's or bot's first name |
| `last_name` | `str` | Optional. User's or bot's last name |
| `username` | `str` | Optional. User's or bot's username |
| `language_code` | `str` | Optional. IETF language tag of the user's language |
| `is_premium` | `bool` | Optional. True, if this user is a Telegram Premium user |
| `added_to_attachment_menu` | `bool` | Optional. True, if this user added the bot to the attachment menu |
| `can_join_groups` | `bool` | Optional. True, if the bot can be invited to groups. Returned only in getMe. |
| `can_read_all_group_messages` | `bool` | Optional. True, if privacy mode is disabled for the bot. Returned only in getMe. |
| `supports_inline_queries` | `bool` | Optional. True, if the bot supports inline queries. Returned only in getMe. |
| `can_connect_to_business` | `bool` | Optional. True, if the bot can be connected to a Telegram Business account to receive its messages. Returned only in getMe. |
| `has_main_web_app` | `bool` | Optional. True, if the bot has a main Web App. Returned only in getMe. |

## Best Practices

1. **Naming**: 
   - Use descriptive class names (`PaymentHandler` vs `Handler1`)
   - Prefix related handlers (`AdminCommands`, `UserCommands`)
