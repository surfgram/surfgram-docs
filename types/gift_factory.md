# GiftsFactory

Factory for creating and managing Gift handlers.

## Usage

The factory automatically registers all active Gift handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a Gift handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_gift`
- **Signature**: `@classmethod def register_gift(cls, gift_cls: Type["Gift"]) -> None`
- **Description**: Registers a new Gift handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["Gift"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
