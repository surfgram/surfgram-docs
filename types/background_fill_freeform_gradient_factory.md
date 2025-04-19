# BackgroundFillFreeformGradientsFactory

Factory for creating and managing BackgroundFillFreeformGradient handlers.

## Usage

The factory automatically registers all active BackgroundFillFreeformGradient handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a BackgroundFillFreeformGradient handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_background_fill_freeform_gradient`
- **Signature**: `@classmethod def register_background_fill_freeform_gradient(cls, background_fill_freeform_gradient_cls: Type["BackgroundFillFreeformGradient"]) -> None`
- **Description**: Registers a new BackgroundFillFreeformGradient handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["BackgroundFillFreeformGradient"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
