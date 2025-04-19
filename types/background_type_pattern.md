# BackgroundTypePattern Handler

Telegram Bot API BackgroundTypePattern type

## Usage

To create a BackgroundTypePattern handler, you need to:

1. Create a class inheriting from `BackgroundTypePattern`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import BackgroundTypePattern
from typing import Callable


class ExampleBackgroundTypePattern(BackgroundTypePattern):
    """Custom handler for BackgroundTypePattern events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_background_type_pattern"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the BackgroundTypePattern event"""
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
    """Processes the BackgroundTypePattern event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `type` (str): Type of the background, always "pattern"
- `document` (Document): Document with the pattern
- `fill` (BackgroundFill): The background fill that is combined with the pattern
- `intensity` (int): Intensity of the pattern when it is shown above the filled background; 0-100
- `is_inverted` (bool): Optional. True, if the background fill must be applied only to the pattern itself. All other pixels are black in this case. For dark themes only
- `is_moving` (bool): Optional. True, if the background moves slightly when the device is tilted
