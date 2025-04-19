# TextQuote Handler

Telegram Bot API TextQuote type

## Usage

To create a TextQuote handler, you need to:

1. Create a class inheriting from `TextQuote`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import TextQuote
from typing import Callable


class ExampleTextQuote(TextQuote):
    """Custom handler for TextQuote events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_text_quote"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the TextQuote event"""
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
    """Processes the TextQuote event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `text` (str): Text of the quoted part of a message that is replied to by the given message
- `entities` (List[MessageEntity]): Optional. Special entities that appear in the quote. Currently, only bold, italic, underline, strikethrough, spoiler, and custom_emoji entities are kept in quotes.
- `position` (int): Approximate quote position in the original message in UTF-16 code units as specified by the sender
- `is_manual` (bool): Optional. True, if the quote was chosen manually by the message sender. Otherwise, the quote was added automatically by the server.
