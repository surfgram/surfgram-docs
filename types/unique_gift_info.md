# UniqueGiftInfo Handler

Telegram Bot API UniqueGiftInfo type

## Usage

To create a UniqueGiftInfo handler, you need to:

1. Create a class inheriting from `UniqueGiftInfo`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import UniqueGiftInfo
from typing import Callable


class ExampleUniqueGiftInfo(UniqueGiftInfo):
    """Custom handler for UniqueGiftInfo events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_unique_gift_info"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the UniqueGiftInfo event"""
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
    """Processes the UniqueGiftInfo event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `gift` (UniqueGift): Information about the gift
- `origin` (str): Origin of the gift. Currently, either "upgrade" or "transfer"
- `owned_gift_id` (str): Optional. Unique identifier of the received gift for the bot; only present for gifts received on behalf of business accounts
- `transfer_star_count` (int): Optional. Number of Telegram Stars that must be paid to transfer the gift; omitted if the bot cannot transfer the gift
