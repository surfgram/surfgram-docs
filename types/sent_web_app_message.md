# SentWebAppMessage Handler

Telegram Bot API SentWebAppMessage type

## Usage

To create a SentWebAppMessage handler, you need to:

1. Create a class inheriting from `SentWebAppMessage`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import SentWebAppMessage
from typing import Callable


class ExampleSentWebAppMessage(SentWebAppMessage):
    """Custom handler for SentWebAppMessage events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_sent_web_app_message"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the SentWebAppMessage event"""
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
    """Processes the SentWebAppMessage event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `inline_message_id` (str): Optional. Identifier of the sent inline message. Available only if there is an inline keyboard attached to the message.
