# ChatShared Handler

Telegram Bot API ChatShared type

## Usage

To create a ChatShared handler, you need to:

1. Create a class inheriting from `ChatShared`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import ChatShared
from typing import Callable


class ExampleChatShared(ChatShared):
    """Custom handler for ChatShared events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_chat_shared"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the ChatShared event"""
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
    """Processes the ChatShared event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `request_id` (int): Identifier of the request
- `chat_id` (int): Identifier of the shared chat. This number may have more than 32 significant bits and some programming languages may have difficulty/silent defects in interpreting it. But it has at most 52 significant bits, so a 64-bit integer or double-precision float type are safe for storing this identifier. The bot may not have access to the chat and could be unable to use this identifier, unless the chat is already known to the bot by some other means.
- `title` (str): Optional. Title of the chat, if the title was requested by the bot.
- `username` (str): Optional. Username of the chat, if the username was requested by the bot and available.
- `photo` (List[PhotoSize]): Optional. Available sizes of the chat photo, if the photo was requested by the bot
