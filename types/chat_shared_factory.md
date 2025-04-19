# ChatSharedsFactory

Factory for creating and managing ChatShared handlers.

## Usage

The factory automatically registers all active ChatShared handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a ChatShared handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_chat_shared`
- **Signature**: `@classmethod def register_chat_shared(cls, chat_shared_cls: Type["ChatShared"]) -> None`
- **Description**: Registers a new ChatShared handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["ChatShared"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
