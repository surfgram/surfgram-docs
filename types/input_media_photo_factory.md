# InputMediaPhotosFactory

Factory for creating and managing InputMediaPhoto handlers.

## Usage

The factory automatically registers all active InputMediaPhoto handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a InputMediaPhoto handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_input_media_photo`
- **Signature**: `@classmethod def register_input_media_photo(cls, input_media_photo_cls: Type["InputMediaPhoto"]) -> None`
- **Description**: Registers a new InputMediaPhoto handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["InputMediaPhoto"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
