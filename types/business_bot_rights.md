# BusinessBotRights

Telegram Bot API BusinessBotRights type

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
from surfgram.types import BusinessBotRights

class MyBusinessBotRightsHandler(BusinessBotRights):
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
| `can_reply` | `bool` | Optional. True, if the bot can send and edit messages in the private chats that had incoming messages in the last 24 hours |
| `can_read_messages` | `bool` | Optional. True, if the bot can mark incoming private messages as read |
| `can_delete_sent_messages` | `bool` | Optional. True, if the bot can delete messages sent by the bot |
| `can_delete_all_messages` | `bool` | Optional. True, if the bot can delete all private messages in managed chats |
| `can_edit_name` | `bool` | Optional. True, if the bot can edit the first and last name of the business account |
| `can_edit_bio` | `bool` | Optional. True, if the bot can edit the bio of the business account |
| `can_edit_profile_photo` | `bool` | Optional. True, if the bot can edit the profile photo of the business account |
| `can_edit_username` | `bool` | Optional. True, if the bot can edit the username of the business account |
| `can_change_gift_settings` | `bool` | Optional. True, if the bot can change the privacy settings pertaining to gifts for the business account |
| `can_view_gifts_and_stars` | `bool` | Optional. True, if the bot can view gifts and the amount of Telegram Stars owned by the business account |
| `can_convert_gifts_to_stars` | `bool` | Optional. True, if the bot can convert regular gifts owned by the business account to Telegram Stars |
| `can_transfer_and_upgrade_gifts` | `bool` | Optional. True, if the bot can transfer and upgrade gifts owned by the business account |
| `can_transfer_stars` | `bool` | Optional. True, if the bot can transfer Telegram Stars received by the business account to its own account, or use them to upgrade and transfer gifts |
| `can_manage_stories` | `bool` | Optional. True, if the bot can post, edit and delete stories on behalf of the business account |

## Best Practices

1. **Naming**: 
   - Use descriptive class names (`PaymentHandler` vs `Handler1`)
   - Prefix related handlers (`AdminCommands`, `UserCommands`)
