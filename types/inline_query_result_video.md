# InlineQueryResultVideo Handler

Telegram Bot API InlineQueryResultVideo type

## Usage

To create a InlineQueryResultVideo handler, you need to:

1. Create a class inheriting from `InlineQueryResultVideo`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import InlineQueryResultVideo
from typing import Callable


class ExampleInlineQueryResultVideo(InlineQueryResultVideo):
    """Custom handler for InlineQueryResultVideo events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_inline_query_result_video"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the InlineQueryResultVideo event"""
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
    """Processes the InlineQueryResultVideo event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `type` (str): Type of the result, must be video
- `id` (str): Unique identifier for this result, 1-64 bytes
- `video_url` (str): A valid URL for the embedded video player or video file
- `mime_type` (str): MIME type of the content of the video URL, "text/html" or "video/mp4"
- `thumbnail_url` (str): URL of the thumbnail (JPEG only) for the video
- `title` (str): Title for the result
- `caption` (str): Optional. Caption of the video to be sent, 0-1024 characters after entities parsing
- `parse_mode` (str): Optional. Mode for parsing entities in the video caption. See formatting options for more details.
- `caption_entities` (List[MessageEntity]): Optional. List of special entities that appear in the caption, which can be specified instead of parse_mode
- `show_caption_above_media` (bool): Optional. Pass True, if the caption must be shown above the message media
- `video_width` (int): Optional. Video width
- `video_height` (int): Optional. Video height
- `video_duration` (int): Optional. Video duration in seconds
- `description` (str): Optional. Short description of the result
- `reply_markup` (InlineKeyboardMarkup): Optional. Inline keyboard attached to the message
- `input_message_content` (InputMessageContent): Optional. Content of the message to be sent instead of the video. This field is required if InlineQueryResultVideo is used to send an HTML-page as a result (e.g., a YouTube video).
