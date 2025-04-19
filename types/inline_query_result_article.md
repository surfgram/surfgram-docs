# InlineQueryResultArticle Handler

Telegram Bot API InlineQueryResultArticle type

## Usage

To create a InlineQueryResultArticle handler, you need to:

1. Create a class inheriting from `InlineQueryResultArticle`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import InlineQueryResultArticle
from typing import Callable


class ExampleInlineQueryResultArticle(InlineQueryResultArticle):
    """Custom handler for InlineQueryResultArticle events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_inline_query_result_article"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the InlineQueryResultArticle event"""
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
    """Processes the InlineQueryResultArticle event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `type` (str): Type of the result, must be article
- `id` (str): Unique identifier for this result, 1-64 Bytes
- `title` (str): Title of the result
- `input_message_content` (InputMessageContent): Content of the message to be sent
- `reply_markup` (InlineKeyboardMarkup): Optional. Inline keyboard attached to the message
- `url` (str): Optional. URL of the result
- `description` (str): Optional. Short description of the result
- `thumbnail_url` (str): Optional. Url of the thumbnail for the result
- `thumbnail_width` (int): Optional. Thumbnail width
- `thumbnail_height` (int): Optional. Thumbnail height
