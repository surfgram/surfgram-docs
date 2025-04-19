# UniqueGift Handler

Telegram Bot API UniqueGift type

## Usage

To create a UniqueGift handler, you need to:

1. Create a class inheriting from `UniqueGift`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import UniqueGift
from typing import Callable


class ExampleUniqueGift(UniqueGift):
    """Custom handler for UniqueGift events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_unique_gift"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the UniqueGift event"""
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
    """Processes the UniqueGift event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `base_name` (str): Human-readable name of the regular gift from which this unique gift was upgraded
- `name` (str): Unique name of the gift. This name can be used in https://t.me/nft/... links and story areas
- `number` (int): Unique number of the upgraded gift among gifts upgraded from the same regular gift
- `model` (UniqueGiftModel): Model of the gift
- `symbol` (UniqueGiftSymbol): Symbol of the gift
- `backdrop` (UniqueGiftBackdrop): Backdrop of the gift
