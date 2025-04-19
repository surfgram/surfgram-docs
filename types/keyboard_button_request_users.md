# KeyboardButtonRequestUsers Handler

Telegram Bot API KeyboardButtonRequestUsers type

## Usage

To create a KeyboardButtonRequestUsers handler, you need to:

1. Create a class inheriting from `KeyboardButtonRequestUsers`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import KeyboardButtonRequestUsers
from typing import Callable


class ExampleKeyboardButtonRequestUsers(KeyboardButtonRequestUsers):
    """Custom handler for KeyboardButtonRequestUsers events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_keyboard_button_request_users"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the KeyboardButtonRequestUsers event"""
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
    """Processes the KeyboardButtonRequestUsers event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `request_id` (int): Signed 32-bit identifier of the request that will be received back in the UsersShared object. Must be unique within the message
- `user_is_bot` (bool): Optional. Pass True to request bots, pass False to request regular users. If not specified, no additional restrictions are applied.
- `user_is_premium` (bool): Optional. Pass True to request premium users, pass False to request non-premium users. If not specified, no additional restrictions are applied.
- `max_quantity` (int): Optional. The maximum number of users to be selected; 1-10. Defaults to 1.
- `request_name` (bool): Optional. Pass True to request the users' first and last names
- `request_username` (bool): Optional. Pass True to request the users' usernames
- `request_photo` (bool): Optional. Pass True to request the users' photos
