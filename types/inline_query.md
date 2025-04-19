# InlineQuery Handler

Telegram Bot API InlineQuery type

## Usage

To create a InlineQuery handler, you need to:

1. Create a class inheriting from `InlineQuery`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import InlineQuery
from typing import Callable


class ExampleInlineQuery(InlineQuery):
    """Custom handler for InlineQuery events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_inline_query"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the InlineQuery event"""
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
    """Processes the InlineQuery event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `id` (str): Unique identifier for this query
- `from` (User): Sender
- `query` (str): Text of the query (up to 256 characters)
- `offset` (str): Offset of the results to be returned, can be controlled by the bot
- `chat_type` (str): Optional. Type of the chat from which the inline query was sent. Can be either "sender" for a private chat with the inline query sender, "private", "group", "supergroup", or "channel". The chat type should be always known for requests sent from official clients and most third-party clients, unless the request was sent from a secret chat
- `location` (Location): Optional. Sender location, only for bots that request user location
