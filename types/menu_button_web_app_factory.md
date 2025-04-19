# MenuButtonWebAppsFactory

Factory for creating and managing MenuButtonWebApp handlers.

## Usage

The factory automatically registers all active MenuButtonWebApp handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a MenuButtonWebApp handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_menu_button_web_app`
- **Signature**: `@classmethod def register_menu_button_web_app(cls, menu_button_web_app_cls: Type["MenuButtonWebApp"]) -> None`
- **Description**: Registers a new MenuButtonWebApp handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["MenuButtonWebApp"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
