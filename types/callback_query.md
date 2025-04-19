# CallbackQuery Handler

Telegram Bot API CallbackQuery type

## Usage

To create a CallbackQuery handler, you need to:

1. Create a class inheriting from `CallbackQuery`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import CallbackQuery
from typing import Callable


class ExampleCallbackQuery(CallbackQuery):
    """Custom handler for CallbackQuery events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_callback_query"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the CallbackQuery event"""
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
    """Processes the CallbackQuery event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `id` (str): Unique identifier for this query
- `from` (User): Sender
- `message` (MaybeInaccessibleMessage): Optional. Message sent by the bot with the callback button that originated the query
- `inline_message_id` (str): Optional. Identifier of the message sent via the bot in inline mode, that originated the query.
- `chat_instance` (str): Global identifier, uniquely corresponding to the chat to which the message with the callback button was sent. Useful for high scores in games.
- `data` (str): Optional. Data associated with the callback button. Be aware that the message originated the query can contain no callback buttons with this data.
- `game_short_name` (str): Optional. Short name of a Game to be returned, serves as the unique identifier for the game
