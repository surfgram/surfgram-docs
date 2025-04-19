# VideoChatParticipantsInvitedsFactory

Factory for creating and managing VideoChatParticipantsInvited handlers.

## Usage

The factory automatically registers all active VideoChatParticipantsInvited handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a VideoChatParticipantsInvited handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_video_chat_participants_invited`
- **Signature**: `@classmethod def register_video_chat_participants_invited(cls, video_chat_participants_invited_cls: Type["VideoChatParticipantsInvited"]) -> None`
- **Description**: Registers a new VideoChatParticipantsInvited handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["VideoChatParticipantsInvited"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
