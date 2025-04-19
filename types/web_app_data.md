# WebAppData Handler

Telegram Bot API WebAppData type

## Usage

To create a WebAppData handler, you need to:

1. Create a class inheriting from `WebAppData`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import WebAppData
from typing import Callable


class ExampleWebAppData(WebAppData):
    """Custom handler for WebAppData events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_web_app_data"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the WebAppData event"""
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
    """Processes the WebAppData event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `data` (str): The data. Be aware that a bad client can send arbitrary data in this field.
- `button_text` (str): Text of the web_app keyboard button from which the Web App was opened. Be aware that a bad client can send arbitrary data in this field.
