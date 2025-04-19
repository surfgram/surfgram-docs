# ChatMemberLeftsFactory

Factory for creating and managing ChatMemberLeft handlers.

## Usage

The factory automatically registers all active ChatMemberLeft handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a ChatMemberLeft handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_chat_member_left`
- **Signature**: `@classmethod def register_chat_member_left(cls, chat_member_left_cls: Type["ChatMemberLeft"]) -> None`
- **Description**: Registers a new ChatMemberLeft handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["ChatMemberLeft"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
