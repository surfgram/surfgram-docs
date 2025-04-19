# ChatPhotosFactory

Factory for creating and managing ChatPhoto handlers.

## Usage

The factory automatically registers all active ChatPhoto handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a ChatPhoto handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_chat_photo`
- **Signature**: `@classmethod def register_chat_photo(cls, chat_photo_cls: Type["ChatPhoto"]) -> None`
- **Description**: Registers a new ChatPhoto handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["ChatPhoto"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
