# ChatBoostSourceGiveaway

Telegram Bot API ChatBoostSourceGiveaway type

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
from surfgram.types import ChatBoostSourceGiveaway

class MyChatBoostSourceGiveawayHandler(ChatBoostSourceGiveaway):    
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
| `source` | `str` | Source of the boost, always "giveaway" |
| `giveaway_message_id` | `int` | Identifier of a message in the chat with the giveaway; the message could have been deleted already. May be 0 if the message isn't sent yet. |
| `user` | `User` | Optional. User that won the prize in the giveaway if any; for Telegram Premium giveaways only |
| `prize_star_count` | `int` | Optional. The number of Telegram Stars to be split between giveaway winners; for Telegram Star giveaways only |
| `is_unclaimed` | `bool` | Optional. True, if the giveaway was completed, but there was no user to win the prize |

## Best Practices

1. **Naming**: 
   - Use descriptive class names (`PaymentHandler` vs `Handler1`)
   - Prefix related handlers (`AdminCommands`, `UserCommands`)
