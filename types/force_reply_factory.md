# ForceRepliesFactory

Factory for creating and managing ForceReply handlers.

## Usage

The factory automatically registers all active ForceReply handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a ForceReply handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_force_reply`
- **Signature**: `@classmethod def register_force_reply(cls, force_reply_cls: Type["ForceReply"]) -> None`
- **Description**: Registers a new ForceReply handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["ForceReply"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
