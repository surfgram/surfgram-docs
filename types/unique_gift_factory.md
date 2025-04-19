# UniqueGiftsFactory

Factory for creating and managing UniqueGift handlers.

## Usage

The factory automatically registers all active UniqueGift handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a UniqueGift handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_unique_gift`
- **Signature**: `@classmethod def register_unique_gift(cls, unique_gift_cls: Type["UniqueGift"]) -> None`
- **Description**: Registers a new UniqueGift handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["UniqueGift"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
