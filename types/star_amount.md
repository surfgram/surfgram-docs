# StarAmount Handler

Telegram Bot API StarAmount type

## Usage

To create a StarAmount handler, you need to:

1. Create a class inheriting from `StarAmount`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import StarAmount
from typing import Callable


class ExampleStarAmount(StarAmount):
    """Custom handler for StarAmount events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_star_amount"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the StarAmount event"""
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
    """Processes the StarAmount event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `amount` (int): Integer amount of Telegram Stars, rounded to 0; can be negative
- `nanostar_amount` (int): Optional. The number of 1/1000000000 shares of Telegram Stars; from -999999999 to 999999999; can be negative if and only if amount is non-positive
