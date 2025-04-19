# User Handler

Telegram Bot API User type

## Usage

To create a User handler, you need to:

1. Create a class inheriting from `User`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import User
from typing import Callable


class ExampleUser(User):
    """Custom handler for User events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_user"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the User event"""
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
    """Processes the User event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `id` (int): Unique identifier for this user or bot. This number may have more than 32 significant bits and some programming languages may have difficulty/silent defects in interpreting it. But it has at most 52 significant bits, so a 64-bit integer or double-precision float type are safe for storing this identifier.
- `is_bot` (bool): True, if this user is a bot
- `first_name` (str): User's or bot's first name
- `last_name` (str): Optional. User's or bot's last name
- `username` (str): Optional. User's or bot's username
- `language_code` (str): Optional. IETF language tag of the user's language
- `is_premium` (bool): Optional. True, if this user is a Telegram Premium user
- `added_to_attachment_menu` (bool): Optional. True, if this user added the bot to the attachment menu
- `can_join_groups` (bool): Optional. True, if the bot can be invited to groups. Returned only in getMe.
- `can_read_all_group_messages` (bool): Optional. True, if privacy mode is disabled for the bot. Returned only in getMe.
- `supports_inline_queries` (bool): Optional. True, if the bot supports inline queries. Returned only in getMe.
- `can_connect_to_business` (bool): Optional. True, if the bot can be connected to a Telegram Business account to receive its messages. Returned only in getMe.
- `has_main_web_app` (bool): Optional. True, if the bot has a main Web App. Returned only in getMe.
