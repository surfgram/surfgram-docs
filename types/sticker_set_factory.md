# StickerSetsFactory

Factory for creating and managing StickerSet handlers.

## Usage

The factory automatically registers all active StickerSet handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a StickerSet handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_sticker_set`
- **Signature**: `@classmethod def register_sticker_set(cls, sticker_set_cls: Type["StickerSet"]) -> None`
- **Description**: Registers a new StickerSet handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["StickerSet"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
