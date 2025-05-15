# GiveawayCompleted

Telegram Bot API GiveawayCompleted type

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
from surfgram.types import GiveawayCompleted

class MyGiveawayCompletedHandler(GiveawayCompleted):    
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
| `winner_count` | `int` | Number of winners in the giveaway |
| `unclaimed_prize_count` | `int` | Optional. Number of undistributed prizes |
| `giveaway_message` | `Message` | Optional. Message with the giveaway that was completed, if it wasn't deleted |
| `is_star_giveaway` | `bool` | Optional. True, if the giveaway is a Telegram Star giveaway. Otherwise, currently, the giveaway is a Telegram Premium giveaway. |

## Best Practices

1. **Naming**: 
   - Use descriptive class names (`PaymentHandler` vs `Handler1`)
   - Prefix related handlers (`AdminCommands`, `UserCommands`)
