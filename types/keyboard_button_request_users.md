# KeyboardButtonRequestUsers

Telegram Bot API KeyboardButtonRequestUsers type

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
from surfgram.types import KeyboardButtonRequestUsers

class MyKeyboardButtonRequestUsersHandler(KeyboardButtonRequestUsers):    
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
| `request_id` | `int` | Signed 32-bit identifier of the request that will be received back in the UsersShared object. Must be unique within the message |
| `user_is_bot` | `bool` | Optional. Pass True to request bots, pass False to request regular users. If not specified, no additional restrictions are applied. |
| `user_is_premium` | `bool` | Optional. Pass True to request premium users, pass False to request non-premium users. If not specified, no additional restrictions are applied. |
| `max_quantity` | `int` | Optional. The maximum number of users to be selected; 1-10. Defaults to 1. |
| `request_name` | `bool` | Optional. Pass True to request the users' first and last names |
| `request_username` | `bool` | Optional. Pass True to request the users' usernames |
| `request_photo` | `bool` | Optional. Pass True to request the users' photos |

## Best Practices

1. **Naming**: 
   - Use descriptive class names (`PaymentHandler` vs `Handler1`)
   - Prefix related handlers (`AdminCommands`, `UserCommands`)
