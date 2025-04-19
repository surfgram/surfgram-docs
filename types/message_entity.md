# MessageEntity Handler

Telegram Bot API MessageEntity type

## Usage

To create a MessageEntity handler, you need to:

1. Create a class inheriting from `MessageEntity`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import MessageEntity
from typing import Callable


class ExampleMessageEntity(MessageEntity):
    """Custom handler for MessageEntity events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_message_entity"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the MessageEntity event"""
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
    """Processes the MessageEntity event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `type` (str): Type of the entity. Currently, can be "mention" (@username), "hashtag" (#hashtag or #hashtag@chatusername), "cashtag" ($USD or $USD@chatusername), "bot_command" (/start@jobs_bot), "url" (https://telegram.org), "email" (do-not-reply@telegram.org), "phone_number" (+1-212-555-0123), "bold" (bold text), "italic" (italic text), "underline" (underlined text), "strikethrough" (strikethrough text), "spoiler" (spoiler message), "blockquote" (block quotation), "expandable_blockquote" (collapsed-by-default block quotation), "code" (monowidth string), "pre" (monowidth block), "text_link" (for clickable text URLs), "text_mention" (for users without usernames), "custom_emoji" (for inline custom emoji stickers)
- `offset` (int): Offset in UTF-16 code units to the start of the entity
- `length` (int): Length of the entity in UTF-16 code units
- `url` (str): Optional. For "text_link" only, URL that will be opened after user taps on the text
- `user` (User): Optional. For "text_mention" only, the mentioned user
- `language` (str): Optional. For "pre" only, the programming language of the entity text
- `custom_emoji_id` (str): Optional. For "custom_emoji" only, unique identifier of the custom emoji. Use getCustomEmojiStickers to get full information about the sticker
