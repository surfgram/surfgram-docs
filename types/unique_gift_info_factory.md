# UniqueGiftInfosFactory

Factory for creating and managing UniqueGiftInfo handlers.

## Usage

The factory automatically registers all active UniqueGiftInfo handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a UniqueGiftInfo handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_unique_gift_info`
- **Signature**: `@classmethod def register_unique_gift_info(cls, unique_gift_info_cls: Type["UniqueGiftInfo"]) -> None`
- **Description**: Registers a new UniqueGiftInfo handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["UniqueGiftInfo"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
