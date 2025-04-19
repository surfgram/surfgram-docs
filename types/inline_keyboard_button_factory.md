# InlineKeyboardButtonsFactory

Factory for creating and managing InlineKeyboardButton handlers.

## Usage

The factory automatically registers all active InlineKeyboardButton handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a InlineKeyboardButton handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_inline_keyboard_button`
- **Signature**: `@classmethod def register_inline_keyboard_button(cls, inline_keyboard_button_cls: Type["InlineKeyboardButton"]) -> None`
- **Description**: Registers a new InlineKeyboardButton handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["InlineKeyboardButton"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
