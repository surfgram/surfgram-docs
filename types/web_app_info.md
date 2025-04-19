# WebAppInfo Handler

Telegram Bot API WebAppInfo type

## Usage

To create a WebAppInfo handler, you need to:

1. Create a class inheriting from `WebAppInfo`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import WebAppInfo
from typing import Callable


class ExampleWebAppInfo(WebAppInfo):
    """Custom handler for WebAppInfo events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_web_app_info"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the WebAppInfo event"""
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
    """Processes the WebAppInfo event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `url` (str): An HTTPS URL of a Web App to be opened with additional data as specified in Initializing Web Apps
