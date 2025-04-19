# OwnedGiftsFactory

Factory for creating and managing OwnedGifts handlers.

## Usage

The factory automatically registers all active OwnedGifts handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a OwnedGifts handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_owned_gifts`
- **Signature**: `@classmethod def register_owned_gifts(cls, owned_gifts_cls: Type["OwnedGifts"]) -> None`
- **Description**: Registers a new OwnedGifts handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["OwnedGifts"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
