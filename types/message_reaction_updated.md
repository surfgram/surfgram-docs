# MessageReactionUpdated Handler

Telegram Bot API MessageReactionUpdated type

## Usage

To create a MessageReactionUpdated handler, you need to:

1. Create a class inheriting from `MessageReactionUpdated`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import MessageReactionUpdated
from typing import Callable


class ExampleMessageReactionUpdated(MessageReactionUpdated):
    """Custom handler for MessageReactionUpdated events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_message_reaction_updated"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the MessageReactionUpdated event"""
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
    """Processes the MessageReactionUpdated event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `chat` (Chat): The chat containing the message the user reacted to
- `message_id` (int): Unique identifier of the message inside the chat
- `user` (User): Optional. The user that changed the reaction, if the user isn't anonymous
- `actor_chat` (Chat): Optional. The chat on behalf of which the reaction was changed, if the user is anonymous
- `date` (int): Date of the change in Unix time
- `old_reaction` (List[ReactionType]): Previous list of reaction types that were set by the user
- `new_reaction` (List[ReactionType]): New list of reaction types that have been set by the user
