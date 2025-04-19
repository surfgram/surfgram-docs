# BackgroundTypeChatTheme Handler

Telegram Bot API BackgroundTypeChatTheme type

## Usage

To create a BackgroundTypeChatTheme handler, you need to:

1. Create a class inheriting from `BackgroundTypeChatTheme`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import BackgroundTypeChatTheme
from typing import Callable


class ExampleBackgroundTypeChatTheme(BackgroundTypeChatTheme):
    """Custom handler for BackgroundTypeChatTheme events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_background_type_chat_theme"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the BackgroundTypeChatTheme event"""
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
    """Processes the BackgroundTypeChatTheme event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `type` (str): Type of the background, always "chat_theme"
- `theme_name` (str): Name of the chat theme, which is usually an emoji
