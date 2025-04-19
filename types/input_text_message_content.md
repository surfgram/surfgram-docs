# InputTextMessageContent Handler

Telegram Bot API InputTextMessageContent type

## Usage

To create a InputTextMessageContent handler, you need to:

1. Create a class inheriting from `InputTextMessageContent`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import InputTextMessageContent
from typing import Callable


class ExampleInputTextMessageContent(InputTextMessageContent):
    """Custom handler for InputTextMessageContent events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_input_text_message_content"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the InputTextMessageContent event"""
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
    """Processes the InputTextMessageContent event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `message_text` (str): Text of the message to be sent, 1-4096 characters
- `parse_mode` (str): Optional. Mode for parsing entities in the message text. See formatting options for more details.
- `entities` (List[MessageEntity]): Optional. List of special entities that appear in message text, which can be specified instead of parse_mode
- `link_preview_options` (LinkPreviewOptions): Optional. Link preview generation options for the message
