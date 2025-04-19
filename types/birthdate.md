# Birthdate Handler

Telegram Bot API Birthdate type

## Usage

To create a Birthdate handler, you need to:

1. Create a class inheriting from `Birthdate`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import Birthdate
from typing import Callable


class ExampleBirthdate(Birthdate):
    """Custom handler for Birthdate events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_birthdate"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the Birthdate event"""
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
    """Processes the Birthdate event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `day` (int): Day of the user's birth; 1-31
- `month` (int): Month of the user's birth; 1-12
- `year` (int): Optional. Year of the user's birth
