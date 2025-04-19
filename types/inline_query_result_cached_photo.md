# InlineQueryResultCachedPhoto Handler

Telegram Bot API InlineQueryResultCachedPhoto type

## Usage

To create a InlineQueryResultCachedPhoto handler, you need to:

1. Create a class inheriting from `InlineQueryResultCachedPhoto`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import InlineQueryResultCachedPhoto
from typing import Callable


class ExampleInlineQueryResultCachedPhoto(InlineQueryResultCachedPhoto):
    """Custom handler for InlineQueryResultCachedPhoto events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_inline_query_result_cached_photo"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the InlineQueryResultCachedPhoto event"""
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
    """Processes the InlineQueryResultCachedPhoto event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `type` (str): Type of the result, must be photo
- `id` (str): Unique identifier for this result, 1-64 bytes
- `photo_file_id` (str): A valid file identifier of the photo
- `title` (str): Optional. Title for the result
- `description` (str): Optional. Short description of the result
- `caption` (str): Optional. Caption of the photo to be sent, 0-1024 characters after entities parsing
- `parse_mode` (str): Optional. Mode for parsing entities in the photo caption. See formatting options for more details.
- `caption_entities` (List[MessageEntity]): Optional. List of special entities that appear in the caption, which can be specified instead of parse_mode
- `show_caption_above_media` (bool): Optional. Pass True, if the caption must be shown above the message media
- `reply_markup` (InlineKeyboardMarkup): Optional. Inline keyboard attached to the message
- `input_message_content` (InputMessageContent): Optional. Content of the message to be sent instead of the photo
