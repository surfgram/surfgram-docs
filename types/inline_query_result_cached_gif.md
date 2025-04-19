# InlineQueryResultCachedGif Handler

Telegram Bot API InlineQueryResultCachedGif type

## Usage

To create a InlineQueryResultCachedGif handler, you need to:

1. Create a class inheriting from `InlineQueryResultCachedGif`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import InlineQueryResultCachedGif
from typing import Callable


class ExampleInlineQueryResultCachedGif(InlineQueryResultCachedGif):
    """Custom handler for InlineQueryResultCachedGif events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_inline_query_result_cached_gif"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the InlineQueryResultCachedGif event"""
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
    """Processes the InlineQueryResultCachedGif event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `type` (str): Type of the result, must be gif
- `id` (str): Unique identifier for this result, 1-64 bytes
- `gif_file_id` (str): A valid file identifier for the GIF file
- `title` (str): Optional. Title for the result
- `caption` (str): Optional. Caption of the GIF file to be sent, 0-1024 characters after entities parsing
- `parse_mode` (str): Optional. Mode for parsing entities in the caption. See formatting options for more details.
- `caption_entities` (List[MessageEntity]): Optional. List of special entities that appear in the caption, which can be specified instead of parse_mode
- `show_caption_above_media` (bool): Optional. Pass True, if the caption must be shown above the message media
- `reply_markup` (InlineKeyboardMarkup): Optional. Inline keyboard attached to the message
- `input_message_content` (InputMessageContent): Optional. Content of the message to be sent instead of the GIF animation
- `type` (str): Type of the result, must be mpeg4_gif
- `id` (str): Unique identifier for this result, 1-64 bytes
- `mpeg4_file_id` (str): A valid file identifier for the MPEG4 file
- `title` (str): Optional. Title for the result
- `caption` (str): Optional. Caption of the MPEG-4 file to be sent, 0-1024 characters after entities parsing
- `parse_mode` (str): Optional. Mode for parsing entities in the caption. See formatting options for more details.
- `caption_entities` (List[MessageEntity]): Optional. List of special entities that appear in the caption, which can be specified instead of parse_mode
- `show_caption_above_media` (bool): Optional. Pass True, if the caption must be shown above the message media
- `reply_markup` (InlineKeyboardMarkup): Optional. Inline keyboard attached to the message
- `input_message_content` (InputMessageContent): Optional. Content of the message to be sent instead of the video animation
