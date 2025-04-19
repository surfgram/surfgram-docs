# ReactionCount Handler

Telegram Bot API ReactionCount type

## Usage

To create a ReactionCount handler, you need to:

1. Create a class inheriting from `ReactionCount`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import ReactionCount
from typing import Callable


class ExampleReactionCount(ReactionCount):
    """Custom handler for ReactionCount events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_reaction_count"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the ReactionCount event"""
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
    """Processes the ReactionCount event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `type` (ReactionType): Type of the reaction
- `total_count` (int): Number of times the reaction was added
