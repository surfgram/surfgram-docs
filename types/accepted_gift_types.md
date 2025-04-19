# AcceptedGiftTypes Handler

Telegram Bot API AcceptedGiftTypes type

## Usage

To create a AcceptedGiftTypes handler, you need to:

1. Create a class inheriting from `AcceptedGiftTypes`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import AcceptedGiftTypes
from typing import Callable


class ExampleAcceptedGiftTypes(AcceptedGiftTypes):
    """Custom handler for AcceptedGiftTypes events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_accepted_gift_types"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the AcceptedGiftTypes event"""
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
    """Processes the AcceptedGiftTypes event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `unlimited_gifts` (bool): True, if unlimited regular gifts are accepted
- `limited_gifts` (bool): True, if limited regular gifts are accepted
- `unique_gifts` (bool): True, if unique gifts or gifts that can be upgraded to unique for free are accepted
- `premium_subscription` (bool): True, if a Telegram Premium subscription is accepted
