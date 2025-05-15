# AffiliateInfo

Telegram Bot API AffiliateInfo type

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
from surfgram.types import AffiliateInfo

class MyAffiliateInfoHandler(AffiliateInfo):
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
| `affiliate_user` | `User` | Optional. The bot or the user that received an affiliate commission if it was received by a bot or a user |
| `affiliate_chat` | `Chat` | Optional. The chat that received an affiliate commission if it was received by a chat |
| `commission_per_mille` | `int` | The number of Telegram Stars received by the affiliate for each 1000 Telegram Stars received by the bot from referred users |
| `amount` | `int` | Integer amount of Telegram Stars received by the affiliate from the transaction, rounded to 0; can be negative for refunds |
| `nanostar_amount` | `int` | Optional. The number of 1/1000000000 shares of Telegram Stars received by the affiliate; from -999999999 to 999999999; can be negative for refunds |

## Best Practices

1. **Naming**: 
   - Use descriptive class names (`PaymentHandler` vs `Handler1`)
   - Prefix related handlers (`AdminCommands`, `UserCommands`)
