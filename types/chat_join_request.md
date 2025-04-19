# ChatJoinRequest Handler

Telegram Bot API ChatJoinRequest type

## Usage

To create a ChatJoinRequest handler, you need to:

1. Create a class inheriting from `ChatJoinRequest`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import ChatJoinRequest
from typing import Callable


class ExampleChatJoinRequest(ChatJoinRequest):
    """Custom handler for ChatJoinRequest events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_chat_join_request"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the ChatJoinRequest event"""
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
    """Processes the ChatJoinRequest event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `chat` (Chat): Chat to which the request was sent
- `from` (User): User that sent the join request
- `user_chat_id` (int): Identifier of a private chat with the user who sent the join request. This number may have more than 32 significant bits and some programming languages may have difficulty/silent defects in interpreting it. But it has at most 52 significant bits, so a 64-bit integer or double-precision float type are safe for storing this identifier. The bot can use this identifier for 5 minutes to send messages until the join request is processed, assuming no other administrator contacted the user.
- `date` (int): Date the request was sent in Unix time
- `bio` (str): Optional. Bio of the user.
- `invite_link` (ChatInviteLink): Optional. Chat invite link that was used by the user to send the join request
