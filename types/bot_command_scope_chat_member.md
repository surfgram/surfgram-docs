# BotCommandScopeChatMember Handler

Telegram Bot API BotCommandScopeChatMember type

## Usage

To create a BotCommandScopeChatMember handler, you need to:

1. Create a class inheriting from `BotCommandScopeChatMember`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import BotCommandScopeChatMember
from typing import Callable


class ExampleBotCommandScopeChatMember(BotCommandScopeChatMember):
    """Custom handler for BotCommandScopeChatMember events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_bot_command_scope_chat_member"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the BotCommandScopeChatMember event"""
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
    """Processes the BotCommandScopeChatMember event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `type` (str): Scope type, must be chat_member
- `chat_id` (Union[int, str]): Unique identifier for the target chat or username of the target supergroup (in the format @supergroupusername)
- `user_id` (int): Unique identifier of the target user
