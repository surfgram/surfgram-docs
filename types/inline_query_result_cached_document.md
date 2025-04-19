# InlineQueryResultCachedDocument Handler

Telegram Bot API InlineQueryResultCachedDocument type

## Usage

To create a InlineQueryResultCachedDocument handler, you need to:

1. Create a class inheriting from `InlineQueryResultCachedDocument`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import InlineQueryResultCachedDocument
from typing import Callable


class ExampleInlineQueryResultCachedDocument(InlineQueryResultCachedDocument):
    """Custom handler for InlineQueryResultCachedDocument events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_inline_query_result_cached_document"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the InlineQueryResultCachedDocument event"""
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
    """Processes the InlineQueryResultCachedDocument event
    
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
- `document_file_id` (str): A valid file identifier for the file
- `description` (str): Optional. Short description of the result
- `caption` (str): Optional. Caption of the document to be sent, 0-1024 characters after entities parsing
- `parse_mode` (str): Optional. Mode for parsing entities in the document caption. See formatting options for more details.
- `caption_entities` (List[MessageEntity]): Optional. List of special entities that appear in the caption, which can be specified instead of parse_mode
- `reply_markup` (InlineKeyboardMarkup): Optional. Inline keyboard attached to the message
- `input_message_content` (InputMessageContent): Optional. Content of the message to be sent instead of the file
