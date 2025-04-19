# InputPaidMediaPhoto Handler

Telegram Bot API InputPaidMediaPhoto type

## Usage

To create a InputPaidMediaPhoto handler, you need to:

1. Create a class inheriting from `InputPaidMediaPhoto`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import InputPaidMediaPhoto
from typing import Callable


class ExampleInputPaidMediaPhoto(InputPaidMediaPhoto):
    """Custom handler for InputPaidMediaPhoto events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_input_paid_media_photo"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the InputPaidMediaPhoto event"""
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
    """Processes the InputPaidMediaPhoto event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `type` (str): Type of the media, must be photo
- `media` (str): File to send. Pass a file_id to send a file that exists on the Telegram servers (recommended), pass an HTTP URL for Telegram to get a file from the Internet, or pass "attach://<file_attach_name>" to upload a new one using multipart/form-data under <file_attach_name> name. More information on Sending Files »
