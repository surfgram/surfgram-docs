# PhotoSizesFactory

Factory for creating and managing PhotoSize handlers.

## Usage

The factory automatically registers all active PhotoSize handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a PhotoSize handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_photo_size`
- **Signature**: `@classmethod def register_photo_size(cls, photo_size_cls: Type["PhotoSize"]) -> None`
- **Description**: Registers a new PhotoSize handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["PhotoSize"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
