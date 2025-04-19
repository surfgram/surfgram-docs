# InputMediaPhoto Handler

Telegram Bot API InputMediaPhoto type

## Usage

To create a InputMediaPhoto handler, you need to:

1. Create a class inheriting from `InputMediaPhoto`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import InputMediaPhoto
from typing import Callable


class ExampleInputMediaPhoto(InputMediaPhoto):
    """Custom handler for InputMediaPhoto events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_input_media_photo"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the InputMediaPhoto event"""
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
    """Processes the InputMediaPhoto event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `type` (str): Type of the result, must be photo
- `media` (str): File to send. Pass a file_id to send a file that exists on the Telegram servers (recommended), pass an HTTP URL for Telegram to get a file from the Internet, or pass "attach://<file_attach_name>" to upload a new one using multipart/form-data under <file_attach_name> name. More information on Sending Files »
- `caption` (str): Optional. Caption of the photo to be sent, 0-1024 characters after entities parsing
- `parse_mode` (str): Optional. Mode for parsing entities in the photo caption. See formatting options for more details.
- `caption_entities` (List[MessageEntity]): Optional. List of special entities that appear in the caption, which can be specified instead of parse_mode
- `show_caption_above_media` (bool): Optional. Pass True, if the caption must be shown above the message media
- `has_spoiler` (bool): Optional. Pass True if the photo needs to be covered with a spoiler animation
