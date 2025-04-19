# InlineKeyboardMarkup Handler

Telegram Bot API InlineKeyboardMarkup type

## Usage

To create a InlineKeyboardMarkup handler, you need to:

1. Create a class inheriting from `InlineKeyboardMarkup`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import InlineKeyboardMarkup
from typing import Callable


class ExampleInlineKeyboardMarkup(InlineKeyboardMarkup):
    """Custom handler for InlineKeyboardMarkup events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_inline_keyboard_markup"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the InlineKeyboardMarkup event"""
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
    """Processes the InlineKeyboardMarkup event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `inline_keyboard` (List[InlineKeyboardButton]): Array of button rows, each represented by an Array of InlineKeyboardButton objects
