# Update

Telegram Bot API Update type

## Overview

| Property        | Type               | Required | Default | Description                              |
|-----------------|--------------------|----------|---------|------------------------------------------|
| `__is_active__` | `bool`             | No       | `True`  | Global handler switch                   |
| `__names__`     | `List[str]`        | No       | `[]`    | Trigger filter (empty = all)            |
| `__callback__`  | `Callable`         | **Yes**  | -       | Async handler function                  |

## Implementation Guide

### Basic Template

```python
from typing import List, Callable
from surfgram.types import Update

class MyUpdateHandler(Update):    
    @property
    def __is_active__(self) -> bool:
        return True  # Set False to disable
        
    @property
    def __names__(self) -> List[str]:
        return []  # ['specific_trigger'] for filtered handling
        
    @property
    def __callback__(self) -> Callable:
        return self.process_event
        
    async def process_event(self, update: dict, bot) -> None:
        """Main handler logic"""
        # Implement your processing here
```

### Field Reference

The update object contains these fields:

| Field          | Type              | Description                     |
|----------------|-------------------|---------------------------------|
| `update_id` | `int` | The update's unique identifier. Update identifiers start from a certain positive number and increase sequentially. This identifier becomes especially handy if you're using webhooks, since it allows you to ignore repeated updates or to restore the correct update sequence, should they get out of order. If there are no new updates for at least a week, then identifier of the next update will be chosen randomly instead of sequentially. |
| `message` | `Message` | Optional. New incoming message of any kind - text, photo, sticker, etc. |
| `edited_message` | `Message` | Optional. New version of a message that is known to the bot and was edited. This update may at times be triggered by changes to message fields that are either unavailable or not actively used by your bot. |
| `channel_post` | `Message` | Optional. New incoming channel post of any kind - text, photo, sticker, etc. |
| `edited_channel_post` | `Message` | Optional. New version of a channel post that is known to the bot and was edited. This update may at times be triggered by changes to message fields that are either unavailable or not actively used by your bot. |
| `business_connection` | `BusinessConnection` | Optional. The bot was connected to or disconnected from a business account, or a user edited an existing connection with the bot |
| `business_message` | `Message` | Optional. New message from a connected business account |
| `edited_business_message` | `Message` | Optional. New version of a message from a connected business account |
| `deleted_business_messages` | `BusinessMessagesDeleted` | Optional. Messages were deleted from a connected business account |
| `message_reaction` | `MessageReactionUpdated` | Optional. A reaction to a message was changed by a user. The bot must be an administrator in the chat and must explicitly specify "message_reaction" in the list of allowed_updates to receive these updates. The update isn't received for reactions set by bots. |
| `message_reaction_count` | `MessageReactionCountUpdated` | Optional. Reactions to a message with anonymous reactions were changed. The bot must be an administrator in the chat and must explicitly specify "message_reaction_count" in the list of allowed_updates to receive these updates. The updates are grouped and can be sent with delay up to a few minutes. |
| `inline_query` | `InlineQuery` | Optional. New incoming inline query |
| `chosen_inline_result` | `ChosenInlineResult` | Optional. The result of an inline query that was chosen by a user and sent to their chat partner. Please see our documentation on the feedback collecting for details on how to enable these updates for your bot. |
| `callback_query` | `CallbackQuery` | Optional. New incoming callback query |
| `shipping_query` | `ShippingQuery` | Optional. New incoming shipping query. Only for invoices with flexible price |
| `pre_checkout_query` | `PreCheckoutQuery` | Optional. New incoming pre-checkout query. Contains full information about checkout |
| `purchased_paid_media` | `PaidMediaPurchased` | Optional. A user purchased paid media with a non-empty payload sent by the bot in a non-channel chat |
| `poll` | `Poll` | Optional. New poll state. Bots receive only updates about manually stopped polls and polls, which are sent by the bot |
| `poll_answer` | `PollAnswer` | Optional. A user changed their answer in a non-anonymous poll. Bots receive new votes only in polls that were sent by the bot itself. |
| `my_chat_member` | `Union[ChatMemberOwner, ChatMemberAdministrator, ChatMemberMember, ChatMemberRestricted, ChatMemberLeft, ChatMemberBanned]` | Optional. The bot's chat member status was updated in a chat. For private chats, this update is received only when the bot is blocked or unblocked by the user. |
| `chat_member` | `Union[ChatMemberOwner, ChatMemberAdministrator, ChatMemberMember, ChatMemberRestricted, ChatMemberLeft, ChatMemberBanned]` | Optional. A chat member's status was updated in a chat. The bot must be an administrator in the chat and must explicitly specify "chat_member" in the list of allowed_updates to receive these updates. |
| `chat_join_request` | `ChatJoinRequest` | Optional. A request to join the chat has been sent. The bot must have the can_invite_users administrator right in the chat to receive these updates. |
| `chat_boost` | `ChatBoostUpdated` | Optional. A chat boost was added or changed. The bot must be an administrator in the chat to receive these updates. |
| `removed_chat_boost` | `ChatBoostRemoved` | Optional. A boost was removed from a chat. The bot must be an administrator in the chat to receive these updates. |

## Best Practices

1. **Naming**: 
   - Use descriptive class names (`PaymentHandler` vs `Handler1`)
   - Prefix related handlers (`AdminCommands`, `UserCommands`)
