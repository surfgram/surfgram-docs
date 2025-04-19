# SwitchInlineQueryChosenChat Handler

Telegram Bot API SwitchInlineQueryChosenChat type

## Usage

To create a SwitchInlineQueryChosenChat handler, you need to:

1. Create a class inheriting from `SwitchInlineQueryChosenChat`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import SwitchInlineQueryChosenChat
from typing import Callable


class ExampleSwitchInlineQueryChosenChat(SwitchInlineQueryChosenChat):
    """Custom handler for SwitchInlineQueryChosenChat events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_switch_inline_query_chosen_chat"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the SwitchInlineQueryChosenChat event"""
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
    """Processes the SwitchInlineQueryChosenChat event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `query` (str): Optional. The default inline query to be inserted in the input field. If left empty, only the bot's username will be inserted
- `allow_user_chats` (bool): Optional. True, if private chats with users can be chosen
- `allow_bot_chats` (bool): Optional. True, if private chats with bots can be chosen
- `allow_group_chats` (bool): Optional. True, if group and supergroup chats can be chosen
- `allow_channel_chats` (bool): Optional. True, if channel chats can be chosen
