# InlineQueryResultContact Handler

Telegram Bot API InlineQueryResultContact type

## Usage

To create a InlineQueryResultContact handler, you need to:

1. Create a class inheriting from `InlineQueryResultContact`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import InlineQueryResultContact
from typing import Callable


class ExampleInlineQueryResultContact(InlineQueryResultContact):
    """Custom handler for InlineQueryResultContact events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_inline_query_result_contact"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the InlineQueryResultContact event"""
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
    """Processes the InlineQueryResultContact event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `type` (str): Type of the result, must be contact
- `id` (str): Unique identifier for this result, 1-64 Bytes
- `phone_number` (str): Contact's phone number
- `first_name` (str): Contact's first name
- `last_name` (str): Optional. Contact's last name
- `vcard` (str): Optional. Additional data about the contact in the form of a vCard, 0-2048 bytes
- `reply_markup` (InlineKeyboardMarkup): Optional. Inline keyboard attached to the message
- `input_message_content` (InputMessageContent): Optional. Content of the message to be sent instead of the contact
- `thumbnail_url` (str): Optional. Url of the thumbnail for the result
- `thumbnail_width` (int): Optional. Thumbnail width
- `thumbnail_height` (int): Optional. Thumbnail height
