# ChatMemberUpdatedsFactory

Factory for creating and managing ChatMemberUpdated handlers.

## Usage

The factory automatically registers all active ChatMemberUpdated handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a ChatMemberUpdated handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_chat_member_updated`
- **Signature**: `@classmethod def register_chat_member_updated(cls, chat_member_updated_cls: Type["ChatMemberUpdated"]) -> None`
- **Description**: Registers a new ChatMemberUpdated handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["ChatMemberUpdated"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
