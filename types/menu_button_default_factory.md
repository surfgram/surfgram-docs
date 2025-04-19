# MenuButtonDefaultsFactory

Factory for creating and managing MenuButtonDefault handlers.

## Usage

The factory automatically registers all active MenuButtonDefault handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a MenuButtonDefault handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_menu_button_default`
- **Signature**: `@classmethod def register_menu_button_default(cls, menu_button_default_cls: Type["MenuButtonDefault"]) -> None`
- **Description**: Registers a new MenuButtonDefault handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["MenuButtonDefault"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
