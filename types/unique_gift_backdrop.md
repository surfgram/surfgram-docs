# UniqueGiftBackdrop Handler

Telegram Bot API UniqueGiftBackdrop type

## Usage

To create a UniqueGiftBackdrop handler, you need to:

1. Create a class inheriting from `UniqueGiftBackdrop`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import UniqueGiftBackdrop
from typing import Callable


class ExampleUniqueGiftBackdrop(UniqueGiftBackdrop):
    """Custom handler for UniqueGiftBackdrop events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_unique_gift_backdrop"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the UniqueGiftBackdrop event"""
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
    """Processes the UniqueGiftBackdrop event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `name` (str): Name of the backdrop
- `colors` (Union[UniqueGiftBackdropCol, s]): Colors of the backdrop
- `rarity_per_mille` (int): The number of unique gifts that receive this backdrop for every 1000 gifts upgraded
