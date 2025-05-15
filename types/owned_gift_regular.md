# OwnedGiftRegular

Telegram Bot API OwnedGiftRegular type

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
from surfgram.types import OwnedGiftRegular

class MyOwnedGiftRegularHandler(OwnedGiftRegular):
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
| `type` | `str` | Type of the gift, always "regular" |
| `gift` | `Gift` | Information about the regular gift |
| `owned_gift_id` | `str` | Optional. Unique identifier of the gift for the bot; for gifts received on behalf of business accounts only |
| `sender_user` | `User` | Optional. Sender of the gift if it is a known user |
| `send_date` | `int` | Date the gift was sent in Unix time |
| `text` | `str` | Optional. Text of the message that was added to the gift |
| `entities` | `List[MessageEntity]` | Optional. Special entities that appear in the text |
| `is_private` | `bool` | Optional. True, if the sender and gift text are shown only to the gift receiver; otherwise, everyone will be able to see them |
| `is_saved` | `bool` | Optional. True, if the gift is displayed on the account's profile page; for gifts received on behalf of business accounts only |
| `can_be_upgraded` | `bool` | Optional. True, if the gift can be upgraded to a unique gift; for gifts received on behalf of business accounts only |
| `was_refunded` | `bool` | Optional. True, if the gift was refunded and isn't available anymore |
| `convert_star_count` | `int` | Optional. Number of Telegram Stars that can be claimed by the receiver instead of the gift; omitted if the gift cannot be converted to Telegram Stars |
| `prepaid_upgrade_star_count` | `int` | Optional. Number of Telegram Stars that were paid by the sender for the ability to upgrade the gift |

## Best Practices

1. **Naming**: 
   - Use descriptive class names (`PaymentHandler` vs `Handler1`)
   - Prefix related handlers (`AdminCommands`, `UserCommands`)
