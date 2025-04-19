# ChatMemberAdministrator Handler

Telegram Bot API ChatMemberAdministrator type

## Usage

To create a ChatMemberAdministrator handler, you need to:

1. Create a class inheriting from `ChatMemberAdministrator`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import ChatMemberAdministrator
from typing import Callable


class ExampleChatMemberAdministrator(ChatMemberAdministrator):
    """Custom handler for ChatMemberAdministrator events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_chat_member_administrator"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the ChatMemberAdministrator event"""
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
    """Processes the ChatMemberAdministrator event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `status` (str): The member's status in the chat, always "administrator"
- `user` (User): Information about the user
- `can_be_edited` (bool): True, if the bot is allowed to edit administrator privileges of that user
- `is_anonymous` (bool): True, if the user's presence in the chat is hidden
- `can_manage_chat` (bool): True, if the administrator can access the chat event log, get boost list, see hidden supergroup and channel members, report spam messages and ignore slow mode. Implied by any other administrator privilege.
- `can_delete_messages` (bool): True, if the administrator can delete messages of other users
- `can_manage_video_chats` (bool): True, if the administrator can manage video chats
- `can_restrict_members` (bool): True, if the administrator can restrict, ban or unban chat members, or access supergroup statistics
- `can_promote_members` (bool): True, if the administrator can add new administrators with a subset of their own privileges or demote administrators that they have promoted, directly or indirectly (promoted by administrators that were appointed by the user)
- `can_change_info` (bool): True, if the user is allowed to change the chat title, photo and other settings
- `can_invite_users` (bool): True, if the user is allowed to invite new users to the chat
- `can_post_stories` (bool): True, if the administrator can post stories to the chat
- `can_edit_stories` (bool): True, if the administrator can edit stories posted by other users, post stories to the chat page, pin chat stories, and access the chat's story archive
- `can_delete_stories` (bool): True, if the administrator can delete stories posted by other users
- `can_post_messages` (bool): Optional. True, if the administrator can post messages in the channel, or access channel statistics; for channels only
- `can_edit_messages` (bool): Optional. True, if the administrator can edit messages of other users and can pin messages; for channels only
- `can_pin_messages` (bool): Optional. True, if the user is allowed to pin messages; for groups and supergroups only
- `can_manage_topics` (bool): Optional. True, if the user is allowed to create, rename, close, and reopen forum topics; for supergroups only
- `custom_title` (str): Optional. Custom title for this user
