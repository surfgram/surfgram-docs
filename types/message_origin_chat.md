# MessageOriginChat Handler

Telegram Bot API MessageOriginChat type

## Usage

To create a MessageOriginChat handler, you need to:

1. Create a class inheriting from `MessageOriginChat`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import MessageOriginChat
from typing import Callable


class ExampleMessageOriginChat(MessageOriginChat):
    """Custom handler for MessageOriginChat events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_message_origin_chat"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the MessageOriginChat event"""
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
    """Processes the MessageOriginChat event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `type` (str): Type of the message origin, always "chat"
- `date` (int): Date the message was sent originally in Unix time
- `sender_chat` (Chat): Chat that sent the message originally
- `author_signature` (str): Optional. For messages originally sent by an anonymous chat administrator, original message author signature
