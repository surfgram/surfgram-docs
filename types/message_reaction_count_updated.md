# MessageReactionCountUpdated Handler

Telegram Bot API MessageReactionCountUpdated type

## Usage

To create a MessageReactionCountUpdated handler, you need to:

1. Create a class inheriting from `MessageReactionCountUpdated`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import MessageReactionCountUpdated
from typing import Callable


class ExampleMessageReactionCountUpdated(MessageReactionCountUpdated):
    """Custom handler for MessageReactionCountUpdated events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_message_reaction_count_updated"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the MessageReactionCountUpdated event"""
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
    """Processes the MessageReactionCountUpdated event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `chat` (Chat): The chat containing the message
- `message_id` (int): Unique message identifier inside the chat
- `date` (int): Date of the change in Unix time
- `reactions` (List[ReactionCount]): List of reactions that are present on the message
