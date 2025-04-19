# BusinessIntro Handler

Telegram Bot API BusinessIntro type

## Usage

To create a BusinessIntro handler, you need to:

1. Create a class inheriting from `BusinessIntro`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import BusinessIntro
from typing import Callable


class ExampleBusinessIntro(BusinessIntro):
    """Custom handler for BusinessIntro events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_business_intro"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the BusinessIntro event"""
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
    """Processes the BusinessIntro event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `title` (str): Optional. Title text of the business intro
- `message` (str): Optional. Message text of the business intro
- `sticker` (Sticker): Optional. Sticker of the business intro
