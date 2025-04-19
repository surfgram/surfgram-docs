# Dice Handler

Telegram Bot API Dice type

## Usage

To create a Dice handler, you need to:

1. Create a class inheriting from `Dice`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import Dice
from typing import Callable


class ExampleDice(Dice):
    """Custom handler for Dice events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_dice"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the Dice event"""
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
    """Processes the Dice event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `emoji` (str): Emoji on which the dice throw animation is based
- `value` (int): Value of the dice, 1-6 for "", "" and "" base emoji, 1-5 for "" and "" base emoji, 1-64 for "" base emoji
