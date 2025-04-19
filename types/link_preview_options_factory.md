# LinkPreviewOptionsFactory

Factory for creating and managing LinkPreviewOptions handlers.

## Usage

The factory automatically registers all active LinkPreviewOptions handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a LinkPreviewOptions handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_link_preview_options`
- **Signature**: `@classmethod def register_link_preview_options(cls, link_preview_options_cls: Type["LinkPreviewOptions"]) -> None`
- **Description**: Registers a new LinkPreviewOptions handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["LinkPreviewOptions"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
