# ResponseParameters Handler

Telegram Bot API ResponseParameters type

## Usage

To create a ResponseParameters handler, you need to:

1. Create a class inheriting from `ResponseParameters`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import ResponseParameters
from typing import Callable


class ExampleResponseParameters(ResponseParameters):
    """Custom handler for ResponseParameters events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_response_parameters"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the ResponseParameters event"""
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
    """Processes the ResponseParameters event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `migrate_to_chat_id` (int): Optional. The group has been migrated to a supergroup with the specified identifier. This number may have more than 32 significant bits and some programming languages may have difficulty/silent defects in interpreting it. But it has at most 52 significant bits, so a signed 64-bit integer or double-precision float type are safe for storing this identifier.
- `retry_after` (int): Optional. In case of exceeding flood control, the number of seconds left to wait before the request can be repeated
