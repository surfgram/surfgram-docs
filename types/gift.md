# Gift Handler

Telegram Bot API Gift type

## Usage

To create a Gift handler, you need to:

1. Create a class inheriting from `Gift`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import Gift
from typing import Callable


class ExampleGift(Gift):
    """Custom handler for Gift events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_gift"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the Gift event"""
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
    """Processes the Gift event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `id` (str): Unique identifier of the gift
- `sticker` (Sticker): The sticker that represents the gift
- `star_count` (int): The number of Telegram Stars that must be paid to send the sticker
- `upgrade_star_count` (int): Optional. The number of Telegram Stars that must be paid to upgrade the gift to a unique one
- `total_count` (int): Optional. The total number of the gifts of this type that can be sent; for limited gifts only
- `remaining_count` (int): Optional. The number of remaining gifts of this type that can be sent; for limited gifts only
