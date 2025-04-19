# PaidMediaPreviewsFactory

Factory for creating and managing PaidMediaPreview handlers.

## Usage

The factory automatically registers all active PaidMediaPreview handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a PaidMediaPreview handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_paid_media_preview`
- **Signature**: `@classmethod def register_paid_media_preview(cls, paid_media_preview_cls: Type["PaidMediaPreview"]) -> None`
- **Description**: Registers a new PaidMediaPreview handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["PaidMediaPreview"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
