# ChatInviteLink

Telegram Bot API ChatInviteLink type

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
from surfgram.types import ChatInviteLink

class MyChatInviteLinkHandler(ChatInviteLink):    
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
| `invite_link` | `str` | The invite link. If the link was created by another chat administrator, then the second part of the link will be replaced with "…". |
| `creator` | `User` | Creator of the link |
| `creates_join_request` | `bool` | True, if users joining the chat via the link need to be approved by chat administrators |
| `is_primary` | `bool` | True, if the link is primary |
| `is_revoked` | `bool` | True, if the link is revoked |
| `name` | `str` | Optional. Invite link name |
| `expire_date` | `int` | Optional. Point in time (Unix timestamp) when the link will expire or has been expired |
| `member_limit` | `int` | Optional. The maximum number of users that can be members of the chat simultaneously after joining the chat via this invite link; 1-99999 |
| `pending_join_request_count` | `int` | Optional. Number of pending join requests created using this link |
| `subscription_period` | `int` | Optional. The number of seconds the subscription will be active for before the next payment |
| `subscription_price` | `int` | Optional. The amount of Telegram Stars a user must pay initially and after each subsequent subscription period to be a member of the chat using the link |

## Best Practices

1. **Naming**: 
   - Use descriptive class names (`PaymentHandler` vs `Handler1`)
   - Prefix related handlers (`AdminCommands`, `UserCommands`)
