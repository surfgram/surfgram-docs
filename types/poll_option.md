# PollOption Handler

Telegram Bot API PollOption type

## Usage

To create a PollOption handler, you need to:

1. Create a class inheriting from `PollOption`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import PollOption
from typing import Callable


class ExamplePollOption(PollOption):
    """Custom handler for PollOption events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_poll_option"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the PollOption event"""
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
    """Processes the PollOption event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `text` (str): Option text, 1-100 characters
- `text_entities` (List[MessageEntity]): Optional. Special entities that appear in the option text. Currently, only custom emoji entities are allowed in poll option texts
- `voter_count` (int): Number of users that voted for this option
