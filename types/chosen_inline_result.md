# ChosenInlineResult Handler

Telegram Bot API ChosenInlineResult type

## Usage

To create a ChosenInlineResult handler, you need to:

1. Create a class inheriting from `ChosenInlineResult`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import ChosenInlineResult
from typing import Callable


class ExampleChosenInlineResult(ChosenInlineResult):
    """Custom handler for ChosenInlineResult events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_chosen_inline_result"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the ChosenInlineResult event"""
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
    """Processes the ChosenInlineResult event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `result_id` (str): The unique identifier for the result that was chosen
- `from` (User): The user that chose the result
- `location` (Location): Optional. Sender location, only for bots that require user location
- `inline_message_id` (str): Optional. Identifier of the sent inline message. Available only if there is an inline keyboard attached to the message. Will be also received in callback queries and can be used to edit the message.
- `query` (str): The query that was used to obtain the result
