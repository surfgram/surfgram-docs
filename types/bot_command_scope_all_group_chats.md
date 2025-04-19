# BotCommandScopeAllGroupChats Handler

Telegram Bot API BotCommandScopeAllGroupChats type

## Usage

To create a BotCommandScopeAllGroupChats handler, you need to:

1. Create a class inheriting from `BotCommandScopeAllGroupChats`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import BotCommandScopeAllGroupChats
from typing import Callable


class ExampleBotCommandScopeAllGroupChats(BotCommandScopeAllGroupChats):
    """Custom handler for BotCommandScopeAllGroupChats events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_bot_command_scope_all_group_chats"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the BotCommandScopeAllGroupChats event"""
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
    """Processes the BotCommandScopeAllGroupChats event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `type` (str): Scope type, must be all_group_chats
