# OwnedGiftUnique

Telegram Bot API OwnedGiftUnique type

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
from surfgram.types import OwnedGiftUnique

class MyOwnedGiftUniqueHandler(OwnedGiftUnique):
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
| `type` | `str` | Type of the gift, always "unique" |
| `gift` | `UniqueGift` | Information about the unique gift |
| `owned_gift_id` | `str` | Optional. Unique identifier of the received gift for the bot; for gifts received on behalf of business accounts only |
| `sender_user` | `User` | Optional. Sender of the gift if it is a known user |
| `send_date` | `int` | Date the gift was sent in Unix time |
| `is_saved` | `bool` | Optional. True, if the gift is displayed on the account's profile page; for gifts received on behalf of business accounts only |
| `can_be_transferred` | `bool` | Optional. True, if the gift can be transferred to another owner; for gifts received on behalf of business accounts only |
| `transfer_star_count` | `int` | Optional. Number of Telegram Stars that must be paid to transfer the gift; omitted if the bot cannot transfer the gift |

## Best Practices

1. **Naming**: 
   - Use descriptive class names (`PaymentHandler` vs `Handler1`)
   - Prefix related handlers (`AdminCommands`, `UserCommands`)
