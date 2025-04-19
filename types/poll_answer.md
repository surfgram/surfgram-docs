# PollAnswer Handler

Telegram Bot API PollAnswer type

## Usage

To create a PollAnswer handler, you need to:

1. Create a class inheriting from `PollAnswer`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import PollAnswer
from typing import Callable


class ExamplePollAnswer(PollAnswer):
    """Custom handler for PollAnswer events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_poll_answer"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the PollAnswer event"""
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
    """Processes the PollAnswer event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `poll_id` (str): Unique poll identifier
- `voter_chat` (Chat): Optional. The chat that changed the answer to the poll, if the voter is anonymous
- `user` (User): Optional. The user that changed the answer to the poll, if the voter isn't anonymous
- `option_ids` (List[int]): 0-based identifiers of chosen answer options. May be empty if the vote was retracted.
