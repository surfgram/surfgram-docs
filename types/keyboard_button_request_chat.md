# KeyboardButtonRequestChat Handler

Telegram Bot API KeyboardButtonRequestChat type

## Usage

To create a KeyboardButtonRequestChat handler, you need to:

1. Create a class inheriting from `KeyboardButtonRequestChat`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import KeyboardButtonRequestChat
from typing import Callable


class ExampleKeyboardButtonRequestChat(KeyboardButtonRequestChat):
    """Custom handler for KeyboardButtonRequestChat events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_keyboard_button_request_chat"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the KeyboardButtonRequestChat event"""
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
    """Processes the KeyboardButtonRequestChat event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `request_id` (int): Signed 32-bit identifier of the request, which will be received back in the ChatShared object. Must be unique within the message
- `chat_is_channel` (bool): Pass True to request a channel chat, pass False to request a group or a supergroup chat.
- `chat_is_forum` (bool): Optional. Pass True to request a forum supergroup, pass False to request a non-forum chat. If not specified, no additional restrictions are applied.
- `chat_has_username` (bool): Optional. Pass True to request a supergroup or a channel with a username, pass False to request a chat without a username. If not specified, no additional restrictions are applied.
- `chat_is_created` (bool): Optional. Pass True to request a chat owned by the user. Otherwise, no additional restrictions are applied.
- `user_administrator_rights` (Union[ChatAdministrat, Rights]): Optional. A JSON-serialized object listing the required administrator rights of the user in the chat. The rights must be a superset of bot_administrator_rights. If not specified, no additional restrictions are applied.
- `bot_administrator_rights` (Union[ChatAdministrat, Rights]): Optional. A JSON-serialized object listing the required administrator rights of the bot in the chat. The rights must be a subset of user_administrator_rights. If not specified, no additional restrictions are applied.
- `bot_is_member` (bool): Optional. Pass True to request a chat with the bot as a member. Otherwise, no additional restrictions are applied.
- `request_title` (bool): Optional. Pass True to request the chat's title
- `request_username` (bool): Optional. Pass True to request the chat's username
- `request_photo` (bool): Optional. Pass True to request the chat's photo
