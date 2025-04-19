# PaidMediaPhotosFactory

Factory for creating and managing PaidMediaPhoto handlers.

## Usage

The factory automatically registers all active PaidMediaPhoto handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a PaidMediaPhoto handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_paid_media_photo`
- **Signature**: `@classmethod def register_paid_media_photo(cls, paid_media_photo_cls: Type["PaidMediaPhoto"]) -> None`
- **Description**: Registers a new PaidMediaPhoto handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["PaidMediaPhoto"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
