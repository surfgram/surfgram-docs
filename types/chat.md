# Chat Handler

Telegram Bot API Chat type

## Usage

To create a Chat handler, you need to:

1. Create a class inheriting from `Chat`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import Chat
from typing import Callable


class ExampleChat(Chat):
    """Custom handler for Chat events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_chat"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the Chat event"""
        # Your implementation here
        pass
```

## Required Properties

### `__names__`
- **Type**: `List[str]`
- **Description**: List of trigger names that will activate this handler
- **Example**: `return ["start", "begin"]`

### `__callback__`
- **Type**: `Callable`
- **Description**: Returns the async function that will process the event
- **Signature**: `async def callback(update, bot) -> None`

## Handler Method

Your handler method should have the following signature:

```python
async def handle(self, update, bot):
    """Processes the Chat event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `id` (int): Unique identifier for this chat. This number may have more than 32 significant bits and some programming languages may have difficulty/silent defects in interpreting it. But it has at most 52 significant bits, so a signed 64-bit integer or double-precision float type are safe for storing this identifier.
- `type` (str): Type of the chat, can be either "private", "group", "supergroup" or "channel"
- `title` (str): Optional. Title, for supergroups, channels and group chats
- `username` (str): Optional. Username, for private chats, supergroups and channels if available
- `first_name` (str): Optional. First name of the other party in a private chat
- `last_name` (str): Optional. Last name of the other party in a private chat
- `is_forum` (bool): Optional. True, if the supergroup chat is a forum (has topics enabled)
