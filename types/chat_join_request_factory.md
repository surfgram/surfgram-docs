# ChatJoinRequestsFactory

Factory for creating and managing ChatJoinRequest handlers.

## Usage

The factory automatically registers all active ChatJoinRequest handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a ChatJoinRequest handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_chat_join_request`
- **Signature**: `@classmethod def register_chat_join_request(cls, chat_join_request_cls: Type["ChatJoinRequest"]) -> None`
- **Description**: Registers a new ChatJoinRequest handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["ChatJoinRequest"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
