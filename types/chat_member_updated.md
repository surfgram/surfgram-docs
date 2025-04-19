# ChatMemberUpdated Handler

Telegram Bot API ChatMemberUpdated type

## Usage

To create a ChatMemberUpdated handler, you need to:

1. Create a class inheriting from `ChatMemberUpdated`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import ChatMemberUpdated
from typing import Callable


class ExampleChatMemberUpdated(ChatMemberUpdated):
    """Custom handler for ChatMemberUpdated events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_chat_member_updated"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the ChatMemberUpdated event"""
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
    """Processes the ChatMemberUpdated event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `chat` (Chat): Chat the user belongs to
- `from` (User): Performer of the action, which resulted in the change
- `date` (int): Date the change was done in Unix time
- `old_chat_member` (Union[ChatMemberOwner, ChatMemberAdministrator, ChatMemberMember, ChatMemberRestricted, ChatMemberLeft, ChatMemberBanned]): Previous information about the chat member
- `new_chat_member` (Union[ChatMemberOwner, ChatMemberAdministrator, ChatMemberMember, ChatMemberRestricted, ChatMemberLeft, ChatMemberBanned]): New information about the chat member
- `invite_link` (ChatInviteLink): Optional. Chat invite link, which was used by the user to join the chat; for joining by invite link events only.
- `via_join_request` (bool): Optional. True, if the user joined the chat after sending a direct join request without using an invite link and being approved by an administrator
- `via_chat_folder_invite_link` (bool): Optional. True, if the user joined the chat via a chat folder invite link
