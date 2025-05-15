# Giveaway

Telegram Bot API Giveaway type

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
from surfgram.types import Giveaway

class MyGiveawayHandler(Giveaway):
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
| `chats` | `List[Chat]` | The list of chats which the user must join to participate in the giveaway |
| `winners_selection_date` | `int` | Point in time (Unix timestamp) when winners of the giveaway will be selected |
| `winner_count` | `int` | The number of users which are supposed to be selected as winners of the giveaway |
| `only_new_members` | `bool` | Optional. True, if only users who join the chats after the giveaway started should be eligible to win |
| `has_public_winners` | `bool` | Optional. True, if the list of giveaway winners will be visible to everyone |
| `prize_description` | `str` | Optional. Description of additional giveaway prize |
| `country_codes` | `List[str]` | Optional. A list of two-letter ISO 3166-1 alpha-2 country codes indicating the countries from which eligible users for the giveaway must come. If empty, then all users can participate in the giveaway. Users with a phone number that was bought on Fragment can always participate in giveaways. |
| `prize_star_count` | `int` | Optional. The number of Telegram Stars to be split between giveaway winners; for Telegram Star giveaways only |
| `premium_subscription_month_count` | `int` | Optional. The number of months the Telegram Premium subscription won from the giveaway will be active for; for Telegram Premium giveaways only |

## Best Practices

1. **Naming**: 
   - Use descriptive class names (`PaymentHandler` vs `Handler1`)
   - Prefix related handlers (`AdminCommands`, `UserCommands`)
