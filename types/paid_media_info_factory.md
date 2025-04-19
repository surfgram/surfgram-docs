# PaidMediaInfosFactory

Factory for creating and managing PaidMediaInfo handlers.

## Usage

The factory automatically registers all active PaidMediaInfo handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a PaidMediaInfo handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_paid_media_info`
- **Signature**: `@classmethod def register_paid_media_info(cls, paid_media_info_cls: Type["PaidMediaInfo"]) -> None`
- **Description**: Registers a new PaidMediaInfo handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["PaidMediaInfo"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
