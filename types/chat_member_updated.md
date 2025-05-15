# ChatMemberUpdated

Telegram Bot API ChatMemberUpdated type

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
from surfgram.types import ChatMemberUpdated

class MyChatMemberUpdatedHandler(ChatMemberUpdated):
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
| `chat` | `Chat` | Chat the user belongs to |
| `from` | `User` | Performer of the action, which resulted in the change |
| `date` | `int` | Date the change was done in Unix time |
| `old_chat_member` | `Union[ChatMemberOwner, ChatMemberAdministrator, ChatMemberMember, ChatMemberRestricted, ChatMemberLeft, ChatMemberBanned]` | Previous information about the chat member |
| `new_chat_member` | `Union[ChatMemberOwner, ChatMemberAdministrator, ChatMemberMember, ChatMemberRestricted, ChatMemberLeft, ChatMemberBanned]` | New information about the chat member |
| `invite_link` | `ChatInviteLink` | Optional. Chat invite link, which was used by the user to join the chat; for joining by invite link events only. |
| `via_join_request` | `bool` | Optional. True, if the user joined the chat after sending a direct join request without using an invite link and being approved by an administrator |
| `via_chat_folder_invite_link` | `bool` | Optional. True, if the user joined the chat via a chat folder invite link |

## Best Practices

1. **Naming**: 
   - Use descriptive class names (`PaymentHandler` vs `Handler1`)
   - Prefix related handlers (`AdminCommands`, `UserCommands`)
