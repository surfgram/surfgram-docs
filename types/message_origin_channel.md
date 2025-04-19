# MessageOriginChannel Handler

Telegram Bot API MessageOriginChannel type

## Usage

To create a MessageOriginChannel handler, you need to:

1. Create a class inheriting from `MessageOriginChannel`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import MessageOriginChannel
from typing import Callable


class ExampleMessageOriginChannel(MessageOriginChannel):
    """Custom handler for MessageOriginChannel events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_message_origin_channel"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the MessageOriginChannel event"""
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
    """Processes the MessageOriginChannel event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `type` (str): Type of the message origin, always "channel"
- `date` (int): Date the message was sent originally in Unix time
- `chat` (Chat): Channel chat to which the message was originally sent
- `message_id` (int): Unique message identifier inside the chat
- `author_signature` (str): Optional. Signature of the original post author
