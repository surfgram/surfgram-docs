# GiveawayCreated Handler

Telegram Bot API GiveawayCreated type

## Usage

To create a GiveawayCreated handler, you need to:

1. Create a class inheriting from `GiveawayCreated`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import GiveawayCreated
from typing import Callable


class ExampleGiveawayCreated(GiveawayCreated):
    """Custom handler for GiveawayCreated events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_giveaway_created"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the GiveawayCreated event"""
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
    """Processes the GiveawayCreated event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `prize_star_count` (int): Optional. The number of Telegram Stars to be split between giveaway winners; for Telegram Star giveaways only
