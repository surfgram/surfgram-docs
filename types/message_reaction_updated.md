# MessageReactionUpdated

Telegram Bot API MessageReactionUpdated type

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
from surfgram.types import MessageReactionUpdated

class MyMessageReactionUpdatedHandler(MessageReactionUpdated):
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
| `chat` | `Chat` | The chat containing the message the user reacted to |
| `message_id` | `int` | Unique identifier of the message inside the chat |
| `user` | `User` | Optional. The user that changed the reaction, if the user isn't anonymous |
| `actor_chat` | `Chat` | Optional. The chat on behalf of which the reaction was changed, if the user is anonymous |
| `date` | `int` | Date of the change in Unix time |
| `old_reaction` | `List[ReactionType]` | Previous list of reaction types that were set by the user |
| `new_reaction` | `List[ReactionType]` | New list of reaction types that have been set by the user |

## Best Practices

1. **Naming**: 
   - Use descriptive class names (`PaymentHandler` vs `Handler1`)
   - Prefix related handlers (`AdminCommands`, `UserCommands`)
