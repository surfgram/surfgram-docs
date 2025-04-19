# ReplyParameters Handler

Telegram Bot API ReplyParameters type

## Usage

To create a ReplyParameters handler, you need to:

1. Create a class inheriting from `ReplyParameters`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import ReplyParameters
from typing import Callable


class ExampleReplyParameters(ReplyParameters):
    """Custom handler for ReplyParameters events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_reply_parameters"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the ReplyParameters event"""
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
    """Processes the ReplyParameters event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `message_id` (int): Identifier of the message that will be replied to in the current chat, or in the chat chat_id if it is specified
- `chat_id` (Union[int, str]): Optional. If the message to be replied to is from a different chat, unique identifier for the chat or username of the channel (in the format @channelusername). Not supported for messages sent on behalf of a business account.
- `allow_sending_without_reply` (bool): Optional. Pass True if the message should be sent even if the specified message to be replied to is not found. Always False for replies in another chat or forum topic. Always True for messages sent on behalf of a business account.
- `quote` (str): Optional. Quoted part of the message to be replied to; 0-1024 characters after entities parsing. The quote must be an exact substring of the message to be replied to, including bold, italic, underline, strikethrough, spoiler, and custom_emoji entities. The message will fail to send if the quote isn't found in the original message.
- `quote_parse_mode` (str): Optional. Mode for parsing entities in the quote. See formatting options for more details.
- `quote_entities` (List[MessageEntity]): Optional. A JSON-serialized list of special entities that appear in the quote. It can be specified instead of quote_parse_mode.
- `quote_position` (int): Optional. Position of the quote in the original message in UTF-16 code units
