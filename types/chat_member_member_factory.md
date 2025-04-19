# ChatMemberMembersFactory

Factory for creating and managing ChatMemberMember handlers.

## Usage

The factory automatically registers all active ChatMemberMember handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a ChatMemberMember handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_chat_member_member`
- **Signature**: `@classmethod def register_chat_member_member(cls, chat_member_member_cls: Type["ChatMemberMember"]) -> None`
- **Description**: Registers a new ChatMemberMember handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["ChatMemberMember"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
