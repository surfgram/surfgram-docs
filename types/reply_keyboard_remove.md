# ReplyKeyboardRemove Handler

Telegram Bot API ReplyKeyboardRemove type

## Usage

To create a ReplyKeyboardRemove handler, you need to:

1. Create a class inheriting from `ReplyKeyboardRemove`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import ReplyKeyboardRemove
from typing import Callable


class ExampleReplyKeyboardRemove(ReplyKeyboardRemove):
    """Custom handler for ReplyKeyboardRemove events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_reply_keyboard_remove"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the ReplyKeyboardRemove event"""
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
    """Processes the ReplyKeyboardRemove event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `remove_keyboard` (bool): Requests clients to remove the custom keyboard (user will not be able to summon this keyboard; if you want to hide the keyboard from sight but keep it accessible, use one_time_keyboard in ReplyKeyboardMarkup)
- `selective` (bool): Optional. Use this parameter if you want to remove the keyboard for specific users only. Targets: 1) users that are @mentioned in the text of the Message object; 2) if the bot's message is a reply to a message in the same chat and forum topic, sender of the original message.Example: A user votes in a poll, bot returns confirmation message in reply to the vote and removes the keyboard for that user, while still showing the keyboard with poll options to users who haven't voted yet.
