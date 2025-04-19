# KeyboardButtonRequestChatsFactory

Factory for creating and managing KeyboardButtonRequestChat handlers.

## Usage

The factory automatically registers all active KeyboardButtonRequestChat handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a KeyboardButtonRequestChat handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_keyboard_button_request_chat`
- **Signature**: `@classmethod def register_keyboard_button_request_chat(cls, keyboard_button_request_chat_cls: Type["KeyboardButtonRequestChat"]) -> None`
- **Description**: Registers a new KeyboardButtonRequestChat handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["KeyboardButtonRequestChat"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
