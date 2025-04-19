# InlineQueryResultCachedSticker Handler

Telegram Bot API InlineQueryResultCachedSticker type

## Usage

To create a InlineQueryResultCachedSticker handler, you need to:

1. Create a class inheriting from `InlineQueryResultCachedSticker`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import InlineQueryResultCachedSticker
from typing import Callable


class ExampleInlineQueryResultCachedSticker(InlineQueryResultCachedSticker):
    """Custom handler for InlineQueryResultCachedSticker events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_inline_query_result_cached_sticker"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the InlineQueryResultCachedSticker event"""
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
    """Processes the InlineQueryResultCachedSticker event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `type` (str): Type of the result, must be sticker
- `id` (str): Unique identifier for this result, 1-64 bytes
- `sticker_file_id` (str): A valid file identifier of the sticker
- `reply_markup` (InlineKeyboardMarkup): Optional. Inline keyboard attached to the message
- `input_message_content` (InputMessageContent): Optional. Content of the message to be sent instead of the sticker
