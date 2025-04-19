# InputStickersFactory

Factory for creating and managing InputSticker handlers.

## Usage

The factory automatically registers all active InputSticker handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a InputSticker handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_input_sticker`
- **Signature**: `@classmethod def register_input_sticker(cls, input_sticker_cls: Type["InputSticker"]) -> None`
- **Description**: Registers a new InputSticker handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["InputSticker"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
