# GiftInfosFactory

Factory for creating and managing GiftInfo handlers.

## Usage

The factory automatically registers all active GiftInfo handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a GiftInfo handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_gift_info`
- **Signature**: `@classmethod def register_gift_info(cls, gift_info_cls: Type["GiftInfo"]) -> None`
- **Description**: Registers a new GiftInfo handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["GiftInfo"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
