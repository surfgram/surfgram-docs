# UniqueGiftBackdropsFactory

Factory for creating and managing UniqueGiftBackdrop handlers.

## Usage

The factory automatically registers all active UniqueGiftBackdrop handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a UniqueGiftBackdrop handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_unique_gift_backdrop`
- **Signature**: `@classmethod def register_unique_gift_backdrop(cls, unique_gift_backdrop_cls: Type["UniqueGiftBackdrop"]) -> None`
- **Description**: Registers a new UniqueGiftBackdrop handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["UniqueGiftBackdrop"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
