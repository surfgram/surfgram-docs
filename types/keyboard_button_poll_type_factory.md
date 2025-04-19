# KeyboardButtonPollTypesFactory

Factory for creating and managing KeyboardButtonPollType handlers.

## Usage

The factory automatically registers all active KeyboardButtonPollType handlers. 
You typically don't need to interact with it directly.

## Registration Flow

1. When a KeyboardButtonPollType handler class is defined:
   - The metaclass checks if `__is_active__` is True
   - If active, registers the handler with the factory
   - Registration uses the names returned by `__names__`

## Methods

### `register_keyboard_button_poll_type`
- **Signature**: `@classmethod def register_keyboard_button_poll_type(cls, keyboard_button_poll_type_cls: Type["KeyboardButtonPollType"]) -> None`
- **Description**: Registers a new KeyboardButtonPollType handler class

### `create`
- **Signature**: `@classmethod async def create(cls, update) -> Optional["KeyboardButtonPollType"]`
- **Description**: Instantiates the appropriate handler based on update content
- **Returns**: Handler instance or None if no match found
