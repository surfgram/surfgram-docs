# ChatMemberRestrictedsFactory

Factory for creating and managing ChatMemberRestricted handlers.

## Usage

The factory automatically registers all active ChatMemberRestricted handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a ChatMemberRestricted handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_chat_member_restricted`
- **Signature**: `@classmethod def register_chat_member_restricted(cls, chat_member_restricted_cls: Type["ChatMemberRestricted"]) -> None`
- **Description**: Registers a new ChatMemberRestricted handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["ChatMemberRestricted"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
