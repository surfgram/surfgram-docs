# WriteAccessAllowed Handler

Telegram Bot API WriteAccessAllowed type

## Usage

To create a WriteAccessAllowed handler, you need to:

1. Create a class inheriting from `WriteAccessAllowed`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import WriteAccessAllowed
from typing import Callable


class ExampleWriteAccessAllowed(WriteAccessAllowed):
    """Custom handler for WriteAccessAllowed events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_write_access_allowed"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the WriteAccessAllowed event"""
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
    """Processes the WriteAccessAllowed event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `from_request` (bool): Optional. True, if the access was granted after the user accepted an explicit request from a Web App sent by the method requestWriteAccess
- `web_app_name` (str): Optional. Name of the Web App, if the access was granted when the Web App was launched from a link
- `from_attachment_menu` (bool): Optional. True, if the access was granted when the bot was added to the attachment or side menu
