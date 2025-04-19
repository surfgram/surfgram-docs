# BackgroundTypeFillsFactory

Factory for creating and managing BackgroundTypeFill handlers.

## Usage

The factory automatically registers all active BackgroundTypeFill handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a BackgroundTypeFill handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_background_type_fill`
- **Signature**: `@classmethod def register_background_type_fill(cls, background_type_fill_cls: Type["BackgroundTypeFill"]) -> None`
- **Description**: Registers a new BackgroundTypeFill handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["BackgroundTypeFill"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
