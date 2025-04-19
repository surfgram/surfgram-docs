# InlineQueryResultDocument Handler

Telegram Bot API InlineQueryResultDocument type

## Usage

To create a InlineQueryResultDocument handler, you need to:

1. Create a class inheriting from `InlineQueryResultDocument`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import InlineQueryResultDocument
from typing import Callable


class ExampleInlineQueryResultDocument(InlineQueryResultDocument):
    """Custom handler for InlineQueryResultDocument events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_inline_query_result_document"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the InlineQueryResultDocument event"""
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
    """Processes the InlineQueryResultDocument event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `type` (str): Type of the result, must be document
- `id` (str): Unique identifier for this result, 1-64 bytes
- `title` (str): Title for the result
- `caption` (str): Optional. Caption of the document to be sent, 0-1024 characters after entities parsing
- `parse_mode` (str): Optional. Mode for parsing entities in the document caption. See formatting options for more details.
- `caption_entities` (List[MessageEntity]): Optional. List of special entities that appear in the caption, which can be specified instead of parse_mode
- `document_url` (str): A valid URL for the file
- `mime_type` (str): MIME type of the content of the file, either "application/pdf" or "application/zip"
- `description` (str): Optional. Short description of the result
- `reply_markup` (InlineKeyboardMarkup): Optional. Inline keyboard attached to the message
- `input_message_content` (InputMessageContent): Optional. Content of the message to be sent instead of the file
- `thumbnail_url` (str): Optional. URL of the thumbnail (JPEG only) for the file
- `thumbnail_width` (int): Optional. Thumbnail width
- `thumbnail_height` (int): Optional. Thumbnail height
