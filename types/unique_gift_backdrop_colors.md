# UniqueGiftBackdropColors Handler

Telegram Bot API UniqueGiftBackdropColors type

## Usage

To create a UniqueGiftBackdropColors handler, you need to:

1. Create a class inheriting from `UniqueGiftBackdropColors`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import UniqueGiftBackdropColors
from typing import Callable


class ExampleUniqueGiftBackdropColors(UniqueGiftBackdropColors):
    """Custom handler for UniqueGiftBackdropColors events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_unique_gift_backdrop_colors"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the UniqueGiftBackdropColors event"""
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
    """Processes the UniqueGiftBackdropColors event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `center_color` (int): The color in the center of the backdrop in RGB format
- `edge_color` (int): The color on the edges of the backdrop in RGB format
- `symbol_color` (int): The color to be applied to the symbol in RGB format
- `text_color` (int): The color for the text on the backdrop in RGB format
