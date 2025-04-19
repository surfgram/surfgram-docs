# UsersShared Handler

Telegram Bot API UsersShared type

## Usage

To create a UsersShared handler, you need to:

1. Create a class inheriting from `UsersShared`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import UsersShared
from typing import Callable


class ExampleUsersShared(UsersShared):
    """Custom handler for UsersShared events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_users_shared"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the UsersShared event"""
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
    """Processes the UsersShared event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `request_id` (int): Identifier of the request
- `users` (List[SharedUser]): Information about users shared with the bot.
