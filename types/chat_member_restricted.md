# ChatMemberRestricted Handler

Telegram Bot API ChatMemberRestricted type

## Usage

To create a ChatMemberRestricted handler, you need to:

1. Create a class inheriting from `ChatMemberRestricted`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import ChatMemberRestricted
from typing import Callable


class ExampleChatMemberRestricted(ChatMemberRestricted):
    """Custom handler for ChatMemberRestricted events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_chat_member_restricted"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the ChatMemberRestricted event"""
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
    """Processes the ChatMemberRestricted event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `status` (str): The member's status in the chat, always "restricted"
- `user` (User): Information about the user
- `is_member` (bool): True, if the user is a member of the chat at the moment of the request
- `can_send_messages` (bool): True, if the user is allowed to send text messages, contacts, giveaways, giveaway winners, invoices, locations and venues
- `can_send_audios` (bool): True, if the user is allowed to send audios
- `can_send_documents` (bool): True, if the user is allowed to send documents
- `can_send_photos` (bool): True, if the user is allowed to send photos
- `can_send_videos` (bool): True, if the user is allowed to send videos
- `can_send_video_notes` (bool): True, if the user is allowed to send video notes
- `can_send_voice_notes` (bool): True, if the user is allowed to send voice notes
- `can_send_polls` (bool): True, if the user is allowed to send polls
- `can_send_other_messages` (bool): True, if the user is allowed to send animations, games, stickers and use inline bots
- `can_add_web_page_previews` (bool): True, if the user is allowed to add web page previews to their messages
- `can_change_info` (bool): True, if the user is allowed to change the chat title, photo and other settings
- `can_invite_users` (bool): True, if the user is allowed to invite new users to the chat
- `can_pin_messages` (bool): True, if the user is allowed to pin messages
- `can_manage_topics` (bool): True, if the user is allowed to create forum topics
- `until_date` (int): Date when restrictions will be lifted for this user; Unix time. If 0, then the user is restricted forever
