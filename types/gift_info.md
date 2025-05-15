# GiftInfo

Telegram Bot API GiftInfo type

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
from surfgram.types import GiftInfo

class MyGiftInfoHandler(GiftInfo):    
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
| `gift` | `Gift` | Information about the gift |
| `owned_gift_id` | `str` | Optional. Unique identifier of the received gift for the bot; only present for gifts received on behalf of business accounts |
| `convert_star_count` | `int` | Optional. Number of Telegram Stars that can be claimed by the receiver by converting the gift; omitted if conversion to Telegram Stars is impossible |
| `prepaid_upgrade_star_count` | `int` | Optional. Number of Telegram Stars that were prepaid by the sender for the ability to upgrade the gift |
| `can_be_upgraded` | `bool` | Optional. True, if the gift can be upgraded to a unique gift |
| `text` | `str` | Optional. Text of the message that was added to the gift |
| `entities` | `List[MessageEntity]` | Optional. Special entities that appear in the text |
| `is_private` | `bool` | Optional. True, if the sender and gift text are shown only to the gift receiver; otherwise, everyone will be able to see them |

## Best Practices

1. **Naming**: 
   - Use descriptive class names (`PaymentHandler` vs `Handler1`)
   - Prefix related handlers (`AdminCommands`, `UserCommands`)
