# BusinessMessagesDeleted Handler

Telegram Bot API BusinessMessagesDeleted type

## Usage

To create a BusinessMessagesDeleted handler, you need to:

1. Create a class inheriting from `BusinessMessagesDeleted`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import BusinessMessagesDeleted
from typing import Callable


class ExampleBusinessMessagesDeleted(BusinessMessagesDeleted):
    """Custom handler for BusinessMessagesDeleted events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_business_messages_deleted"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the BusinessMessagesDeleted event"""
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
    """Processes the BusinessMessagesDeleted event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `business_connection_id` (str): Unique identifier of the business connection
- `chat` (Chat): Information about a chat in the business account. The bot may not have access to the chat or the corresponding user.
- `message_ids` (List[int]): The list of identifiers of deleted messages in the chat of the business account
