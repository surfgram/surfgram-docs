# GiveawayWinners

Telegram Bot API GiveawayWinners type

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
from surfgram.types import GiveawayWinners

class MyGiveawayWinnersHandler(GiveawayWinners):
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
| `chat` | `Chat` | The chat that created the giveaway |
| `giveaway_message_id` | `int` | Identifier of the message with the giveaway in the chat |
| `winners_selection_date` | `int` | Point in time (Unix timestamp) when winners of the giveaway were selected |
| `winner_count` | `int` | Total number of winners in the giveaway |
| `winners` | `List[User]` | List of up to 100 winners of the giveaway |
| `additional_chat_count` | `int` | Optional. The number of other chats the user had to join in order to be eligible for the giveaway |
| `prize_star_count` | `int` | Optional. The number of Telegram Stars that were split between giveaway winners; for Telegram Star giveaways only |
| `premium_subscription_month_count` | `int` | Optional. The number of months the Telegram Premium subscription won from the giveaway will be active for; for Telegram Premium giveaways only |
| `unclaimed_prize_count` | `int` | Optional. Number of undistributed prizes |
| `only_new_members` | `bool` | Optional. True, if only users who had joined the chats after the giveaway started were eligible to win |
| `was_refunded` | `bool` | Optional. True, if the giveaway was canceled because the payment for it was refunded |
| `prize_description` | `str` | Optional. Description of additional giveaway prize |

## Best Practices

1. **Naming**: 
   - Use descriptive class names (`PaymentHandler` vs `Handler1`)
   - Prefix related handlers (`AdminCommands`, `UserCommands`)
