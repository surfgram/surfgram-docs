# OwnedGiftUniquesFactory

Factory for creating and managing OwnedGiftUnique handlers.

## Usage

The factory automatically registers all active OwnedGiftUnique handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a OwnedGiftUnique handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_owned_gift_unique`
- **Signature**: `@classmethod def register_owned_gift_unique(cls, owned_gift_unique_cls: Type["OwnedGiftUnique"]) -> None`
- **Description**: Registers a new OwnedGiftUnique handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["OwnedGiftUnique"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
