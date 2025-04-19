# ChatInviteLinksFactory

Factory for creating and managing ChatInviteLink handlers.

## Usage

The factory automatically registers all active ChatInviteLink handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a ChatInviteLink handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_chat_invite_link`
- **Signature**: `@classmethod def register_chat_invite_link(cls, chat_invite_link_cls: Type["ChatInviteLink"]) -> None`
- **Description**: Registers a new ChatInviteLink handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["ChatInviteLink"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
