# KeyboardButton

Telegram Bot API KeyboardButton type

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
from surfgram.types import KeyboardButton

class MyKeyboardButtonHandler(KeyboardButton):    
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
| `text` | `str` | Text of the button. If none of the optional fields are used, it will be sent as a message when the button is pressed |
| `request_users` | `KeyboardButtonRequestUsers` | Optional. If specified, pressing the button will open a list of suitable users. Identifiers of selected users will be sent to the bot in a "users_shared" service message. Available in private chats only. |
| `request_chat` | `KeyboardButtonRequestChat` | Optional. If specified, pressing the button will open a list of suitable chats. Tapping on a chat will send its identifier to the bot in a "chat_shared" service message. Available in private chats only. |
| `request_contact` | `bool` | Optional. If True, the user's phone number will be sent as a contact when the button is pressed. Available in private chats only. |
| `request_location` | `bool` | Optional. If True, the user's current location will be sent when the button is pressed. Available in private chats only. |
| `request_poll` | `KeyboardButtonPollType` | Optional. If specified, the user will be asked to create a poll and send it to the bot when the button is pressed. Available in private chats only. |
| `web_app` | `WebAppInfo` | Optional. If specified, the described Web App will be launched when the button is pressed. The Web App will be able to send a "web_app_data" service message. Available in private chats only. |

## Best Practices

1. **Naming**: 
   - Use descriptive class names (`PaymentHandler` vs `Handler1`)
   - Prefix related handlers (`AdminCommands`, `UserCommands`)
