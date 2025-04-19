# StickersFactory

Factory for creating and managing Sticker handlers.

## Usage

The factory automatically registers all active Sticker handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a Sticker handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_sticker`
- **Signature**: `@classmethod def register_sticker(cls, sticker_cls: Type["Sticker"]) -> None`
- **Description**: Registers a new Sticker handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["Sticker"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
