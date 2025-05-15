# Gift

Telegram Bot API Gift type

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
from surfgram.types import Gift

class MyGiftHandler(Gift):    
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
| `id` | `str` | Unique identifier of the gift |
| `sticker` | `Sticker` | The sticker that represents the gift |
| `star_count` | `int` | The number of Telegram Stars that must be paid to send the sticker |
| `upgrade_star_count` | `int` | Optional. The number of Telegram Stars that must be paid to upgrade the gift to a unique one |
| `total_count` | `int` | Optional. The total number of the gifts of this type that can be sent; for limited gifts only |
| `remaining_count` | `int` | Optional. The number of remaining gifts of this type that can be sent; for limited gifts only |

## Best Practices

1. **Naming**: 
   - Use descriptive class names (`PaymentHandler` vs `Handler1`)
   - Prefix related handlers (`AdminCommands`, `UserCommands`)
