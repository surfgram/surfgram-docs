# ChatMemberRestricted

Telegram Bot API ChatMemberRestricted type

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
from surfgram.types import ChatMemberRestricted

class MyChatMemberRestrictedHandler(ChatMemberRestricted):
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
| `status` | `str` | The member's status in the chat, always "restricted" |
| `user` | `User` | Information about the user |
| `is_member` | `bool` | True, if the user is a member of the chat at the moment of the request |
| `can_send_messages` | `bool` | True, if the user is allowed to send text messages, contacts, giveaways, giveaway winners, invoices, locations and venues |
| `can_send_audios` | `bool` | True, if the user is allowed to send audios |
| `can_send_documents` | `bool` | True, if the user is allowed to send documents |
| `can_send_photos` | `bool` | True, if the user is allowed to send photos |
| `can_send_videos` | `bool` | True, if the user is allowed to send videos |
| `can_send_video_notes` | `bool` | True, if the user is allowed to send video notes |
| `can_send_voice_notes` | `bool` | True, if the user is allowed to send voice notes |
| `can_send_polls` | `bool` | True, if the user is allowed to send polls |
| `can_send_other_messages` | `bool` | True, if the user is allowed to send animations, games, stickers and use inline bots |
| `can_add_web_page_previews` | `bool` | True, if the user is allowed to add web page previews to their messages |
| `can_change_info` | `bool` | True, if the user is allowed to change the chat title, photo and other settings |
| `can_invite_users` | `bool` | True, if the user is allowed to invite new users to the chat |
| `can_pin_messages` | `bool` | True, if the user is allowed to pin messages |
| `can_manage_topics` | `bool` | True, if the user is allowed to create forum topics |
| `until_date` | `int` | Date when restrictions will be lifted for this user; Unix time. If 0, then the user is restricted forever |

## Best Practices

1. **Naming**: 
   - Use descriptive class names (`PaymentHandler` vs `Handler1`)
   - Prefix related handlers (`AdminCommands`, `UserCommands`)
