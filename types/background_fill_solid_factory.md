# BackgroundFillSolidsFactory

Factory for creating and managing BackgroundFillSolid handlers.

## Usage

The factory automatically registers all active BackgroundFillSolid handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a BackgroundFillSolid handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_background_fill_solid`
- **Signature**: `@classmethod def register_background_fill_solid(cls, background_fill_solid_cls: Type["BackgroundFillSolid"]) -> None`
- **Description**: Registers a new BackgroundFillSolid handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["BackgroundFillSolid"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
