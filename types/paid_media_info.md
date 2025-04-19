# PaidMediaInfo Handler

Telegram Bot API PaidMediaInfo type

## Usage

To create a PaidMediaInfo handler, you need to:

1. Create a class inheriting from `PaidMediaInfo`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import PaidMediaInfo
from typing import Callable


class ExamplePaidMediaInfo(PaidMediaInfo):
    """Custom handler for PaidMediaInfo events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_paid_media_info"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the PaidMediaInfo event"""
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
    """Processes the PaidMediaInfo event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `star_count` (int): The number of Telegram Stars that must be paid to buy access to the media
- `paid_media` (List[PaidMedia]): Information about the paid media
