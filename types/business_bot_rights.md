# BusinessBotRights Handler

Telegram Bot API BusinessBotRights type

## Usage

To create a BusinessBotRights handler, you need to:

1. Create a class inheriting from `BusinessBotRights`
2. Implement the required properties
3. Define your callback function

### Example Implementation

```python
from surfgram.types import BusinessBotRights
from typing import Callable


class ExampleBusinessBotRights(BusinessBotRights):
    """Custom handler for BusinessBotRights events"""
    
    @property
    def __names__(self) -> List[str]:
        """List of trigger names for this handler"""
        return ["example_business_bot_rights"]
    
    @property
    def __callback__(self) -> Callable:
        """Returns the handler function"""
        return self.handle
    
    async def handle(self, update, bot):
        """Processes the BusinessBotRights event"""
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
    """Processes the BusinessBotRights event
    
    Args:
        update: The incoming update object
        bot: The bot instance for API calls
    """
```

## Available Fields

The update object will contain these fields (if applicable):

- `can_reply` (bool): Optional. True, if the bot can send and edit messages in the private chats that had incoming messages in the last 24 hours
- `can_read_messages` (bool): Optional. True, if the bot can mark incoming private messages as read
- `can_delete_outgoing_messages` (bool): Optional. True, if the bot can delete messages sent by the bot
- `can_delete_all_messages` (bool): Optional. True, if the bot can delete all private messages in managed chats
- `can_edit_name` (bool): Optional. True, if the bot can edit the first and last name of the business account
- `can_edit_bio` (bool): Optional. True, if the bot can edit the bio of the business account
- `can_edit_profile_photo` (bool): Optional. True, if the bot can edit the profile photo of the business account
- `can_edit_username` (bool): Optional. True, if the bot can edit the username of the business account
- `can_change_gift_settings` (bool): Optional. True, if the bot can change the privacy settings pertaining to gifts for the business account
- `can_view_gifts_and_stars` (bool): Optional. True, if the bot can view gifts and the amount of Telegram Stars owned by the business account
- `can_convert_gifts_to_stars` (bool): Optional. True, if the bot can convert regular gifts owned by the business account to Telegram Stars
- `can_transfer_and_upgrade_gifts` (bool): Optional. True, if the bot can transfer and upgrade gifts owned by the business account
- `can_transfer_stars` (bool): Optional. True, if the bot can transfer Telegram Stars received by the business account to its own account, or use them to upgrade and transfer gifts
- `can_manage_stories` (bool): Optional. True, if the bot can post, edit and delete stories on behalf of the business account
