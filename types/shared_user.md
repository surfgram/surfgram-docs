# SharedUser Handler

Telegram Bot API SharedUser type

## Usage

To create a SharedUser handler, you need to:

1. Create a class inheriting from `SharedUser`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import SharedUser
from typing import Callable


class ExampleSharedUser(SharedUser):
    """Custom handler for SharedUser events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_shared_user"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the SharedUser event"""
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
    """Processes the SharedUser event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `user_id` (int): Identifier of the shared user. This number may have more than 32 significant bits and some programming languages may have difficulty/silent defects in interpreting it. But it has at most 52 significant bits, so 64-bit integers or double-precision float types are safe for storing these identifiers. The bot may not have access to the user and could be unable to use this identifier, unless the user is already known to the bot by some other means.
- `first_name` (str): Optional. First name of the user, if the name was requested by the bot
- `last_name` (str): Optional. Last name of the user, if the name was requested by the bot
- `username` (str): Optional. Username of the user, if the username was requested by the bot
- `photo` (List[PhotoSize]): Optional. Available sizes of the chat photo, if the photo was requested by the bot
