# ChatMemberBannedsFactory

Factory for creating and managing ChatMemberBanned handlers.

## Usage

The factory automatically registers all active ChatMemberBanned handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a ChatMemberBanned handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_chat_member_banned`
- **Signature**: `@classmethod def register_chat_member_banned(cls, chat_member_banned_cls: Type["ChatMemberBanned"]) -> None`
- **Description**: Registers a new ChatMemberBanned handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["ChatMemberBanned"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
