# ChatMemberLeft Handler

Telegram Bot API ChatMemberLeft type

## Usage

To create a ChatMemberLeft handler, you need to:

1. Create a class inheriting from `ChatMemberLeft`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import ChatMemberLeft
from typing import Callable


class ExampleChatMemberLeft(ChatMemberLeft):
    """Custom handler for ChatMemberLeft events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_chat_member_left"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the ChatMemberLeft event"""
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
    """Processes the ChatMemberLeft event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `status` (str): The member's status in the chat, always "left"
- `user` (User): Information about the user
