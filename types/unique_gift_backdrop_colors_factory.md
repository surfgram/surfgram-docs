# UniqueGiftBackdropColorsFactory

Factory for creating and managing UniqueGiftBackdropColors handlers.

## Usage

The factory automatically registers all active UniqueGiftBackdropColors handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a UniqueGiftBackdropColors handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_unique_gift_backdrop_colors`
- **Signature**: `@classmethod def register_unique_gift_backdrop_colors(cls, unique_gift_backdrop_colors_cls: Type["UniqueGiftBackdropColors"]) -> None`
- **Description**: Registers a new UniqueGiftBackdropColors handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["UniqueGiftBackdropColors"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
