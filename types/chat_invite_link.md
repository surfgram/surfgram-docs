# ChatInviteLink Handler

Telegram Bot API ChatInviteLink type

## Usage

To create a ChatInviteLink handler, you need to:

1. Create a class inheriting from `ChatInviteLink`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import ChatInviteLink
from typing import Callable


class ExampleChatInviteLink(ChatInviteLink):
    """Custom handler for ChatInviteLink events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_chat_invite_link"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the ChatInviteLink event"""
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
    """Processes the ChatInviteLink event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `invite_link` (str): The invite link. If the link was created by another chat administrator, then the second part of the link will be replaced with "…".
- `creator` (User): Creator of the link
- `creates_join_request` (bool): True, if users joining the chat via the link need to be approved by chat administrators
- `is_primary` (bool): True, if the link is primary
- `is_revoked` (bool): True, if the link is revoked
- `name` (str): Optional. Invite link name
- `expire_date` (int): Optional. Point in time (Unix timestamp) when the link will expire or has been expired
- `member_limit` (int): Optional. The maximum number of users that can be members of the chat simultaneously after joining the chat via this invite link; 1-99999
- `pending_join_request_count` (int): Optional. Number of pending join requests created using this link
- `subscription_period` (int): Optional. The number of seconds the subscription will be active for before the next payment
- `subscription_price` (int): Optional. The amount of Telegram Stars a user must pay initially and after each subsequent subscription period to be a member of the chat using the link
