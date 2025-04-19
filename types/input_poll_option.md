# InputPollOption Handler

Telegram Bot API InputPollOption type

## Usage

To create a InputPollOption handler, you need to:

1. Create a class inheriting from `InputPollOption`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import InputPollOption
from typing import Callable


class ExampleInputPollOption(InputPollOption):
    """Custom handler for InputPollOption events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_input_poll_option"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the InputPollOption event"""
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
    """Processes the InputPollOption event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `text` (str): Option text, 1-100 characters
- `text_parse_mode` (str): Optional. Mode for parsing entities in the text. See formatting options for more details. Currently, only custom emoji entities are allowed
- `text_entities` (List[MessageEntity]): Optional. A JSON-serialized list of special entities that appear in the poll option text. It can be specified instead of text_parse_mode
