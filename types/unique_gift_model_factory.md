# UniqueGiftModelsFactory

Factory for creating and managing UniqueGiftModel handlers.

## Usage

The factory automatically registers all active UniqueGiftModel handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a UniqueGiftModel handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_unique_gift_model`
- **Signature**: `@classmethod def register_unique_gift_model(cls, unique_gift_model_cls: Type["UniqueGiftModel"]) -> None`
- **Description**: Registers a new UniqueGiftModel handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["UniqueGiftModel"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
