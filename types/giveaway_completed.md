# GiveawayCompleted Handler

Telegram Bot API GiveawayCompleted type

## Usage

To create a GiveawayCompleted handler, you need to:

1. Create a class inheriting from `GiveawayCompleted`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import GiveawayCompleted
from typing import Callable


class ExampleGiveawayCompleted(GiveawayCompleted):
    """Custom handler for GiveawayCompleted events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_giveaway_completed"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the GiveawayCompleted event"""
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
    """Processes the GiveawayCompleted event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `winner_count` (int): Number of winners in the giveaway
- `unclaimed_prize_count` (int): Optional. Number of undistributed prizes
- `giveaway_message` (Message): Optional. Message with the giveaway that was completed, if it wasn't deleted
- `is_star_giveaway` (bool): Optional. True, if the giveaway is a Telegram Star giveaway. Otherwise, currently, the giveaway is a Telegram Premium giveaway.
