# ForceReply Handler

Telegram Bot API ForceReply type

## Usage

To create a ForceReply handler, you need to:

1. Create a class inheriting from `ForceReply`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import ForceReply
from typing import Callable


class ExampleForceReply(ForceReply):
    """Custom handler for ForceReply events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_force_reply"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the ForceReply event"""
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
    """Processes the ForceReply event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `force_reply` (bool): Shows reply interface to the user, as if they manually selected the bot's message and tapped 'Reply'
- `input_field_placeholder` (str): Optional. The placeholder to be shown in the input field when the reply is active; 1-64 characters
- `selective` (bool): Optional. Use this parameter if you want to force reply from specific users only. Targets: 1) users that are @mentioned in the text of the Message object; 2) if the bot's message is a reply to a message in the same chat and forum topic, sender of the original message.
