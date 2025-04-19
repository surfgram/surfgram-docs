# KeyboardButtonPollType Handler

Telegram Bot API KeyboardButtonPollType type

## Usage

To create a KeyboardButtonPollType handler, you need to:

1. Create a class inheriting from `KeyboardButtonPollType`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import KeyboardButtonPollType
from typing import Callable


class ExampleKeyboardButtonPollType(KeyboardButtonPollType):
    """Custom handler for KeyboardButtonPollType events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_keyboard_button_poll_type"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the KeyboardButtonPollType event"""
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
    """Processes the KeyboardButtonPollType event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `type` (str): Optional. If quiz is passed, the user will be allowed to create only polls in the quiz mode. If regular is passed, only regular polls will be allowed. Otherwise, the user will be allowed to create a poll of any type.
