# BusinessConnection Handler

Telegram Bot API BusinessConnection type

## Usage

To create a BusinessConnection handler, you need to:

1. Create a class inheriting from `BusinessConnection`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import BusinessConnection
from typing import Callable


class ExampleBusinessConnection(BusinessConnection):
    """Custom handler for BusinessConnection events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_business_connection"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the BusinessConnection event"""
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
    """Processes the BusinessConnection event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `id` (str): Unique identifier of the business connection
- `user` (User): Business account user that created the business connection
- `user_chat_id` (int): Identifier of a private chat with the user who created the business connection. This number may have more than 32 significant bits and some programming languages may have difficulty/silent defects in interpreting it. But it has at most 52 significant bits, so a 64-bit integer or double-precision float type are safe for storing this identifier.
- `date` (int): Date the connection was established in Unix time
- `rights` (BusinessBotRights): Optional. Rights of the business bot
- `is_enabled` (bool): True, if the connection is active
