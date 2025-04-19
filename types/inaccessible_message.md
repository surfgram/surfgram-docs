# InaccessibleMessage Handler

Telegram Bot API InaccessibleMessage type

## Usage

To create a InaccessibleMessage handler, you need to:

1. Create a class inheriting from `InaccessibleMessage`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import InaccessibleMessage
from typing import Callable


class ExampleInaccessibleMessage(InaccessibleMessage):
    """Custom handler for InaccessibleMessage events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_inaccessible_message"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the InaccessibleMessage event"""
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
    """Processes the InaccessibleMessage event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `chat` (Chat): Chat the message belonged to
- `message_id` (int): Unique message identifier inside the chat
- `date` (int): Always 0. The field can be used to differentiate regular and inaccessible messages.
