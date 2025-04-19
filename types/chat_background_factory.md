# ChatBackgroundsFactory

Factory for creating and managing ChatBackground handlers.

## Usage

The factory automatically registers all active ChatBackground handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a ChatBackground handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_chat_background`
- **Signature**: `@classmethod def register_chat_background(cls, chat_background_cls: Type["ChatBackground"]) -> None`
- **Description**: Registers a new ChatBackground handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["ChatBackground"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
