# UniqueGiftModel Handler

Telegram Bot API UniqueGiftModel type

## Usage

To create a UniqueGiftModel handler, you need to:

1. Create a class inheriting from `UniqueGiftModel`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import UniqueGiftModel
from typing import Callable


class ExampleUniqueGiftModel(UniqueGiftModel):
    """Custom handler for UniqueGiftModel events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_unique_gift_model"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the UniqueGiftModel event"""
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
    """Processes the UniqueGiftModel event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `name` (str): Name of the model
- `sticker` (Sticker): The sticker that represents the unique gift
- `rarity_per_mille` (int): The number of unique gifts that receive this model for every 1000 gifts upgraded
